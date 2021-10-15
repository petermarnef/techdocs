# SQL

## Troubleshooting performance

### Check DB size

``` sql
sp_spaceused 'Schema.Table'
```

### Query to check index size in KB

``` sql
SELECT i.[name] AS IndexName, SUM(s.[used_page_count]) * 8 AS IndexSizeKB
FROM sys.dm_db_partition_stats AS s
INNER JOIN sys.indexes AS i ON s.[object_id] = i.[object_id]
	AND s.[index_id] = i.[index_id]
WHERE i.name LIKE '%<index-name-here>%'
GROUP BY i.[name]
ORDER BY i.[name]
```

Source: https://basitaalishan.com/2012/07/06/find-the-size-of-index-in-sql-server/

### Query to check table size in MB

``` sql
SELECT
s.Name AS SchemaName,
t.Name AS TableName,
p.rows AS RowCounts,
CAST(ROUND((SUM(a.used_pages) / 128.00), 2) AS NUMERIC(36, 2)) AS Used_MB,
CAST(ROUND((SUM(a.total_pages) - SUM(a.used_pages)) / 128.00, 2) AS NUMERIC(36, 2)) AS Unused_MB,
CAST(ROUND((SUM(a.total_pages) / 128.00), 2) AS NUMERIC(36, 2)) AS Total_MB
FROM sys.tables t
INNER JOIN sys.indexes i ON t.OBJECT_ID = i.object_id
INNER JOIN sys.partitions p ON i.object_id = p.OBJECT_ID AND i.index_id = p.index_id
INNER JOIN sys.allocation_units a ON p.partition_id = a.container_id
INNER JOIN sys.schemas s ON t.schema_id = s.schema_id
WHERE t.name like '%<table-name-here>%'
GROUP BY t.Name, s.Name, p.Rows
ORDER BY s.Name, t.Name
```

Source: https://blog.sqlauthority.com/2017/05/25/sql-server-simple-query-list-size-table-row-counts/

### Query to check column size in KB

``` sql
SELECT id, DATALENGTH(<column-name-here>)/1024 AS SizeInKB, JobType, JobStatus, JobException, RetryFromJobId
FROM --<table-name-here>
ORDER BY 2 DESC
```

### Query to check pending connections

``` sql
SELECT
    c.session_id, c.net_transport, c.encrypt_option, s.status,
    c.auth_scheme, s.host_name, s.program_name, s.client_interface_name,
	s.login_name, s.nt_domain,s.nt_user_name, s.original_login_name,
	c.connect_time, s.login_time
FROM sys.dm_exec_connections AS c
JOIN sys.dm_exec_sessions AS s
    ON c.session_id = s.session_id
ORDER BY c.connect_time ASC
```

#### Kill connection

`KILL <session_id>`
