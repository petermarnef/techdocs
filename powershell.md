# How to
## Send a mail command line
```
Send-MailMessage -From 'noreply@test.com' -To 'johndoe@test.com' -Subject 'Test mail' -SmtpServer 'smtp.mail.be'
```

## Pimp the shell
https://gist.github.com/jchandra74/5b0c94385175c7a8d1cb39bc5157365e

## Get environment variables
```Get-Item -Path Env:*```

[ms docs](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_environment_variables?view=powershell-6)

## How to make Powershell remember the SSH key passphrase

https://gist.github.com/danieldogeanu/16c61e9b80345c5837b9e5045a701c99
