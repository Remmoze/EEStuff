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
   - [deleteFriend](#friends-delete)
   - [deleteInvite](#friends-deleteinvite)
   - [createInvite](#friends-create)
   - [answerInvite](#friends-asnwer)
   - [blockUserInvites](#freinds-block)
 - [Extra Info](#extra)

# <a id="mail">Mail System</a>
### <a id="mail-send">"sendMail"</a>
#### Tip:
To get friends use [Friends](#friends) documentation.

__*.Send.*__

| Id   | Type     | Name    | Description
| ---  | ---      | ----    | -----------
| `0`  | `String` | Target  | Friend's name.
| `1`  | `String` | Subject | Subject of the mail.
| `2`  | `String` | Message | Main body of the mail.

__*.Recieve.*__

| Id   | Type      | Name    | Description
| ---  | ---       | ----    | -----------
| `0`  | `Boolean` | Success | Was operation successful.

-- If operation wasn't successful:

| Id   | Type     | Name    | Description
| ---  | ---      | ----    | -----------
| `1`  | `String` | Message | Error message.

### <a id="mail-get">"getMails"</a>

__*.Recieve.*__

| Id      | Type     | Name    | Description
| ---     | ----     | ----    | -----------
| `[...]` | `String` | Id      | The id of the mail.
| `[...]` | `String` | Name    | Sender's name.
| `[...]` | `String` | Subject | The subject of the mail.
| `[...]` | `String` | Message | The message of the mail.

Repeated for each valid mail.

### <a id="mail-delete">"deleteMail"</a>

__*.Send.*__

| Id  | Type     | Name | Description
| --- | ----     | ---- | -----------
| `0` | `String` | Id   | The id of the mail.

# <a id="friends">Friends</a>
### <a id="friends-invites">"getInvitesToMe"</a>

__*.Recieve.*__

| Id      | Type     | Name | Description
| ---     | ----     | ---- | -----------
| `[...]` | `String` | Name | The name of the person who sent the invite.

Repeated for each valid invite.

### <a id="friends-get">"getFriends"</a>

__*.Recieve.*__

| Id      | Type      | Name        | Description
| ---     | ----      | ----        | -----------
| `[...]` | `String`  | Name        | The name of the friend.
| `[...]` | `Boolean` | Online      | Is friend Online.
| `[...]` | `String`  | World Id    | The id of the world friend is in.
| `[...]` | `String`  | World Name  | The Name of the world friend is in.
| `[...]` | `Integer` | Smiley      | The smiley of the friend.
| `[...]` | `Double`  | Last seen   | The time when friend was last seen.
| `[...]` | `Boolean` | Gold Border | Has gold border enabled.

Repeated for each valid friend.

### <a id="friends-pendings">"getPending"</a>

__*.Recieve.*__

| Id      | Type      | Name  | Description
| ---     | ----      | ----  | -----------
| `[...]` | `String`  | Name  | The name of the person.
| `[...]` | `Integer` | State | See Friends state table.

Repeated for each valid pending.

| Value | Friend State
| ----- | ----------
| `0`   | Pending
| `1`   | Accepted
| `2`   | Rejected

### <a id="friends-blocked">"getBlockedUsers"</a>

__*.Recieve.*__

| Id      | Type     | Name | Description
| ---     | ----     | ---- | -----------
| `[...]` | `String` | Name | The name of the blocked person.

### <a id="friends-delete">"deleteFriend"</a>

__*.Send.*__

| Id  | Type     | Name | Description
| --- | ----     | ---- | -----------
| `0` | `String` | Name | The name of the friend you want to delete.

### <a id="friends-deleteinvite">"deleteInvite"</a>

__*.Send.*__

| Id  | Type     | Name | Description
| --- | ----     | ---- | -----------
| `0` | `String` | Name | The name of the person you want to reject.

### <a id="friends-create">"createInvite"</a>

__*.Send.*__

| Id  | Type     | Name | Description
| --- | ----     | ---- | -----------
| `0` | `String` | Name | The name of the person you want to add.

__*.Recieve.*__

| Id   | Type        | Name    | Description
| ---  | ---         | ----    | -----------
| `0`  | `Boolean`   | Success | Was operation successful.

-- If operation wasn't successful:

| Id   | Type        | Name    | Description
| ---  | ---         | ----    | -----------
| `1`  | `String`    | Message | Error message.

### <a id="friends-asnwer">"answerInvite"</a>

__*.Send.*__

| Id  | Type      | Name   | Description
| --- | ----      | ----   | -----------
| `0` | `String`  | Name   | The name of the person.
| `1` | `Boolean` | Answer | Accept or reject the invite.

__*.Recieve.*__

| Id   | Type      | Name    | Description
| ---  | ---       | ----    | -----------
| `0`  | `Boolean` | Success | Was operation successful.

-- If operation wasn't successful:

| Id   | Type     | Name    | Description
| ---  | ---      | ----    | -----------
| `1`  | `String` | Message | Error message.

-- If operation was successful:
Recieves information about new friend. Documentation can be found [here](#friends-get)

### <a id="friends-block">"blockUserInvites"</a>

__*.Send.*__

| Id  | Type      | Name  | Description
| --- | ----      | ----  | -----------
| `0` | `String`  | Name  | The name of the person.
| `1` | `Boolean` | Block | Block or unblock the person.

# <a id="extra">Extra</a>
```
If a message doesn't have .Send. - you don't need extra arguments to send the message.
If a message doesn't have .Recieve. - there is no callback.
```
