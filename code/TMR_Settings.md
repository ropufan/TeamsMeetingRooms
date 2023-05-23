
# Tech notes @ Robert

## Changing the language of a Teams Meeting Rooms

Build a [Microsoft Teams Rooms image - Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/rooms/console#selecting-a-language)

## Enable "Dial Pad" on Teams Meeting Rooms

```powershell
Set-CsPhoneNumberAssignment -Identity mtr@moderncomms559460.onmicrosoft.com -EnterpriseVoiceEnabled $true
```

## Enablement of accepting Meetings from another Organization

```powershell
$SCOPED_USER = "admin@MODERNCOMMS175817.onmicrosoft.com" # Insert your Admin account here
$SCOPED_ROOM = "MTR HUB" # Insert your Meeting Room Name here

Set-ExecutionPolicy RemoteSigned
Install-Module -Name ExchangeOnlineManagement
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $SCOPED_USER
Get-Mailbox -RecipientTypeDetails RoomMailbox 
Get-Mailbox $SCOPED_ROOM | Set-CalendarProcessing -ProcessExternalMeetingMessages $true
```

## Manage sharing with Guests for Microsoft Whiteboard

```powershell
Install-Module Microsoft.Online.SharePoint.PowerShell
Update-Module -Name Microsoft.Online.SharePoint.PowerShell
Connect-SPOService -Credential $creds
Set-SPOTenant -AllowAnonymousMeetingParticipantsToAccessWhiteboards On
```

Ensure that the Teams meeting setting Anonymous users can interact with apps in meetings is enabled. <br>
If you've disabled it, any anonymous users (as opposed to guests or federated users) won't have access to the whiteboard during the meeting.
