<hr />

# EEStuff

Stuff about EE (everybodyedits.com)

```
If a message doesn't have .Send. - you don't need extra arguments to send the message.
If a message doesn't have .Recieve. - there is no callback.
```

# Documentation for Lobby Connection

 - [Shop](#shop)
   - [getShop](#shop-get)
 - [Profiles](#profile)
   - [getProfileObject](#profile-get)
   - [setUsername](#profile-setusername)
   - [changeUsername](#profile-changeusername)
   - [toggleProfile](#profile-toggle)
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
   - [blockAllInvites](#friends-blockall)
 - [Lobby](#lobby)
   - [getLobbyProperties](#lobby-getproperties)
   - [getMySimplePlayerObject](#lobby-getplayerobject)
   - [timezone](#lobby-timezone)
   - [finishTutorial](#lobby-finishtutorial)
   - [acceptTerms](#lobby-acceptterms)
 - [Extra](#extra)
   - [no documentation](#extra-private)

<hr />

# <a id="shop">Shop</a>

### <a id="shop-get">"getShop"</a>

__*.Recieve.*__

| Id  | Type     | Name  | Description
| --- | ---      | ----  | -----------
| `0` | `String` | State | Is profile public.

<hr />

# <a id="profile">Profile</a>

### <a id="profile-get">"getProfileObject"</a>

__*.Send.*__

| Id  | Type     | Name     | Description
| --- | ---      | ----     | -----------
| `0` | `String` | Username | Username of the player you want to get.

__*.Recieve.*__

| Id  | Type     | Name  | Description
| --- | ---      | ----  | -----------
| `0` | `String` | State | Is profile public.

-- If State returns "public":

| Id   | Type      | Name             | Description
| ---  | ---       | ----             | -----------
| `1`  | `String`  | UserId           | The userid of the player.
| `2`  | `String`  | Name             | The name of the player.
| `3`  | `String`  | OldName          | The oldname of the player. (null if name wasn't changed)
| `4`  | `Integer` | Smiley           | The smiley id of the player.
| `5`  | `Integer` | Max Energy       | The max energy of the player.
| `6`  | `Boolean` | Is Old Beta      | Does player own old beta. (?)
| `7`  | `Boolean` | Is Administrator | Is player an admin.
| `8`  | `Boolean` | Is Gold Member   | The smiley id of the player.
| `9`  | `Integer` | Gold Expires     | When does your gold membership expires.
| `10` | `Integer` | Gold Time        | (?)
| `11` | `String`  | Room0            | first room!?! (maybe?)
| `12` | `String`  | Beta only room   | wtf? People can have more than 1 world right? ee is shit
| `13` | `String`  | Home world       | Your home world id.
| `14` | `String`  | Worlds order     | Worlds placed in order spitted by '᎙' (example: "world0x0᎙world0x1᎙world1x1")
| `15` | `String`  | Worlds Ids       | Worlds Ids in the same order splitted by '᎙' (example: "PW01᎙PWabc᎙PWJesse")
| `16` | `String`  | Worlds Names     | Worlds Names in the same order splitted by '᎙' (example: "My Love᎙My Grace᎙My Shrek")

<hr />

### <a id="profile-setusername">"setUsername"</a>

__*.Send.*__

| Id  | Type     | Name         | Description
| --- | ---      | ----         | -----------
| `0` | `String` | Chosen Name  | Name you want to set.

**NOTE:** You need to set your username upon registering a new player.

<hr />

### <a id="profile-changeusername">"changeUsername"</a>

__*.Send.*__

| Id  | Type     | Name         | Description
| --- | ---      | ----         | -----------
| `0` | `String` | Chosen Name  | Name you want to set.

**NOTE:** You need to set your username after buying a namechange.

<hr />

### <a id="profile-toggle">"toggleProfile"</a>

__*.Send.*__

| Id  | Type      | Name  | Description
| --- | ---       | ----  | -----------
| `0` | `Boolean` | State | Desired visibility state for your profile.  

# <a id="mail">Mail System</a>

### <a id="mail-send">"sendMail"</a>

#### Tip:
To get friends use [Friends](#friends) documentation.

__*.Send.*__

| Id  | Type     | Name    | Description
| --- | ---      | ----    | -----------
| `0` | `String` | Target  | Friend's name.
| `1` | `String` | Subject | Subject of the mail.
| `2` | `String` | Message | Main body of the mail.

__*.Recieve.*__

| Id  | Type      | Name    | Description
| --- | ---       | ----    | -----------
| `0` | `Boolean` | Success | Was operation successful.

-- If operation wasn't successful:

| Id  | Type     | Name    | Description
| --- | ---      | ----    | -----------
| `1` | `String` | Message | Error message.

<hr />

### <a id="mail-get">"getMails"</a>

__*.Recieve.*__

| Id      | Type     | Name    | Description
| ---     | ----     | ----    | -----------
| `[...]` | `String` | Id      | The id of the mail.
| `[...]` | `String` | Name    | Sender's name.
| `[...]` | `String` | Subject | The subject of the mail.
| `[...]` | `String` | Message | The message of the mail.

Repeated for each valid mail.

<hr />

### <a id="mail-delete">"deleteMail"</a>

__*.Send.*__

| Id  | Type     | Name | Description
| --- | ----     | ---- | -----------
| `0` | `String` | Id   | The id of the mail.

<hr />

# <a id="friends">Friends</a>

### <a id="friends-invites">"getInvitesToMe"</a>

__*.Recieve.*__

| Id      | Type     | Name | Description
| ---     | ----     | ---- | -----------
| `[...]` | `String` | Name | The name of the person who sent the invite.

Repeated for each valid invite.

<hr />

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

<hr />

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

<hr />

### <a id="friends-blocked">"getBlockedUsers"</a>

__*.Recieve.*__

| Id      | Type     | Name | Description
| ---     | ----     | ---- | -----------
| `[...]` | `String` | Name | The name of the blocked person.

<hr />

### <a id="friends-delete">"deleteFriend"</a>

__*.Send.*__

| Id  | Type     | Name | Description
| --- | ----     | ---- | -----------
| `0` | `String` | Name | The name of the friend you want to delete.

<hr />

### <a id="friends-deleteinvite">"deleteInvite"</a>

__*.Send.*__

| Id  | Type     | Name | Description
| --- | ----     | ---- | -----------
| `0` | `String` | Name | The name of the person you want to reject.

<hr />

### <a id="friends-create">"createInvite"</a>

__*.Send.*__

| Id  | Type     | Name | Description
| --- | ----     | ---- | -----------
| `0` | `String` | Name | The name of the person you want to add.

__*.Recieve.*__

| Id  | Type        | Name    | Description
| --- | ---         | ----    | -----------
| `0` | `Boolean`   | Success | Was operation successful.

-- If operation wasn't successful:

| Id  | Type        | Name    | Description
| --- | ---         | ----    | -----------
| `1` | `String`    | Message | Error message.

<hr />

### <a id="friends-asnwer">"answerInvite"</a>

__*.Send.*__

| Id  | Type      | Name   | Description
| --- | ----      | ----   | -----------
| `0` | `String`  | Name   | The name of the person.
| `1` | `Boolean` | Answer | Accept or reject the invite.

__*.Recieve.*__

| Id  | Type      | Name    | Description
| --- | ---       | ----    | -----------
| `0` | `Boolean` | Success | Was operation successful.

-- If operation wasn't successful:

| Id  | Type     | Name    | Description
| --- | ---      | ----    | -----------
| `1` | `String` | Message | Error message.

-- If operation was successful:
Recieves information about new friend. Documentation can be found [here](#friends-get)

<hr />

### <a id="friends-block">"blockUserInvites"</a>

__*.Send.*__

| Id  | Type      | Name  | Description
| --- | ----      | ----  | -----------
| `0` | `String`  | Name  | The name of the person.
| `1` | `Boolean` | Block | Block or unblock the person.

<hr />

### <a id="friends-blockall">"blockAllInvites"</a>

__*.Recieve.*__

| Id  | Type      | Name  | Description
| --- | ---       | ----  | -----------
| `0` | `Boolean` | State | Blocked all invites.

<hr />

# <a id="lobby">Lobby</a>

<hr />

### <a id="lobby-getproperties">"getLobbyProperties"</a>

__*.Recieve.*__

| Id  | Type      | Name              | Description
| --- | ---       | ----              | -----------
| `0` | `Boolean` | First Daily Login | Is it the first time you login lobby this day.
| `1` | `Integer` | Streak            | Your daily streak.

-- Note: if you want to get a day of the streak you should use `Message.GetInt(1)+1;`

<hr />

### <a id="lobby-getplayerobject">"getMySimplePlayerObject"</a>

__*.Recieve.*__

| Id   | Type      | Name              | Description
| ---  | ---       | ----              | -----------
| `0`  | `String`  | Name              | Your name.
| `1`  | `Integer` | Smiley            | Your smiley id.
| `2`  | `Integer` | Aura              | Your aura id.
| `3`  | `Integer` | Aura color        | Your aura color.
| `4`  | `Boolean` | Chat banned       | Are you a chat banned user.
| `5`  | `Boolean` | Smiley pack       | Has smiley pack. (?) //need to look into that
| `6`  | `Boolean` | Is Administrator  | Are you an admin.
| `7`  | `Boolean` | Is Moderator      | Are you a mod.
| `8`  | `Boolean` | Is Gold Member    | Are you a gold member.
| `9`  | `Boolean` | Wears Gold Border | Are you wearing a gold border.
| `10` | `Integer` | Gold Expires      | When does your gold membership expires.
| `11` | `Integer` | Gold Time         | (?)
| `12` | `Boolean` | Gold Welcome      | (?)
| `13` | `String`  | Room0             | first room!?! (maybe?)
| `14` | `String`  | Beta only room    | wtf? People can have more than 1 world right? ee is shit
| `15` | `String`  | Home world        | Your home world id.
| `16` | `String`  | Worlds order      | Worlds placed in order spitted by '᎙' (example: "world0x0᎙world0x1᎙world1x1")
| `17` | `String`  | Worlds Ids        | Worlds Ids in the same order splitted by '᎙' (example: "PW01᎙PWabc᎙PWJesse")
| `18` | `String`  | Worlds Names      | Worlds Names in the same order splitted by '᎙' (example: "My Love᎙My Grace᎙My Shrek")
| `19` | `Boolean` | Visible           | Visibility of your profile.
| `20` | `Boolean` | Banned            | Are you banned.
| `21` | `Integer` | Accepted Terms    | Have you accepted terms.
| `22` | `Integer` | Tutorial Version  | Your tutorial version.
| `23` | `String`  | Badge             | Name of your current badge.
| `24` | `Integer` | Max Energy        | Your max energy.
| `25` | `Boolean` | Changed Name      | Have you changed your name in the past.
| `26` | `String`  | Favorites Ids     | Your World Favorites Ids spitted by '᎙' (example: "PW01᎙PWOmg᎙PWJesse")
| `27` | `String`  | Favorites names   | Your World Favorites Names spitted by '᎙' (example: "Lol Kek Chebyrek᎙I Love Maxi᎙Jessenoob")

<hr />

### <a id="lobby-timezone">"timezone"</a>

__*.Send.*__

| Id  | Type      | Name        | Description
| --- | ----      | ----        | -----------
| `0` | `Integer` | TimeOffset  | The difference, in minutes, between universal time (UTC) and the computer's local time.

<hr />

### <a id="lobby-finishtutorial">"finishTutorial"</a>

-- No extra information needed.

<hr />

### <a id="lobby-acceptterms">"acceptTerms"</a>

-- No extra information needed.

<hr />

# <a id="extra">Extra</a>

### <a id="extra-private">No documentation.</a>
-- list of messages with no documentation for various reasons
 - "confirmEmail"



