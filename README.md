# EEStuff
Stuff about EE (everybodyedits.com)

# Documentation for Lobby Connection
 - [Mail System](#mail)
   - [sendMail](#mail-send)
   - [getMails](#mail-get)
   - [deleteMail](#mail-delete)
 - [Friends](#friends)
   - [getInvitesToMe](#friends-invites)
   - [getFriends](#friends-get)
   - [getPending](#friends-pendings)
   - [getBlockedUsers](#friends-blocked)
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

### <a id="mail-get">"getMails"</a>

__*.Send.*__ - no extra arguments needed

__*.Recieve.*__

| Id      | Type     | Name          | Description
| ---     | ----     | ----          | -----------
| `[...]` | `String` | Id            | The id of the mail.
| `[...]` | `String` | Name          | Sender's name.
| `[...]` | `String` | Subject       | The subject of the mail.
| `[...]` | `String` | Message       | The message of the mail.

Repeated for each valid mail.

### <a id="mail-delete">"deleteMail"</a>

__*.Send.*__

| Id  | Type     | Name          | Description
| --- | ----     | ----          | -----------
| `0` | `String` | Id            | The id of the mail.

# <a id="friends">Friends</a>
### <a id="friends-invites">"getInvitesToMe"</a>

__*.Send.*__ - no extra arguments needed

__*.Recieve.*__

| Id      | Type     | Name          | Description
| ---     | ----     | ----          | -----------
| `[...]` | `String` | Name          | The name of the person who sent the invite.

Repeated for each valid invite.

### <a id="friends-get">"getFriends"</a>
### <a id="friends-pendings">"getPending"</a>

__*.Send.*__ - no extra arguments needed

__*.Recieve.*__

| Id      | Type     | Name  | Description
| ---     | ----     | ----  | -----------
| `[...]` | `String` | Name  | The name of the person.
| `[...]` | `Integer`| State | See Friends state table.

| Value | Friend State
| ----- | ----------
| `0`   | Pending
| `1`   | Accepted
| `2`   | Rejected

### <a id="friends-blocked">"getBlockedUsers"</a>

__*.Send.*__ - no extra arguments needed

__*.Recieve.*__

| Id      | Type     | Name          | Description
| ---     | ----     | ----          | -----------
| `[...]` | `String` | Name          | The name of the blocked person.

# <a id="extra">Extra</a>
```
no.
```
