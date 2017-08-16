# EEStuff
Stuff about EE (everybodyedits.com)

## Documentation for Lobby Connection
 - [Mail System](#mail)
   - [sendMail](#mail-send)
 - [Extra Info](#extra)

# <a id="mail">Mail System</a>
### <a id="mail-send">"sendMail"</a>
#### Tip:
To get friends use [Friends](#friends) documentation.
__*.Send.*__

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `String`    | Target             | Friend's name.
| `1`  | `String`    | Subject            | Subject of the mail.
| `2`  | `String`    | Message            | Main body of the mail.

__*.Recieve.*__

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `0`  | `Boolean`   | Success            | Was operation successful.

-- If sending message wasn't successful:

| Id   | Type        | Name               | Description
| ---  | ---         | ----               | -----------
| `1`  | `String`    | Message            | Error message.

# <a id="extra">Extra</a>
```
no.
```
