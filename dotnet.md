# How to
## Send mails to local folder
Replace mail settings in web.config with the following:
```
<mailSettings>
    <smtp deliveryMethod="SpecifiedPickupDirectory">
        <specifiedPickupDirectory pickupDirectoryLocation="c:\temp\mails\"/>
    </smtp>
</mailSettings>
```