# 👨‍👩‍👧‍👦 Users
The users are the main entities of the identity service. We will describe the user-related concepts and details in the following.

## Users Entity
The following properties (except password_encrypted and password_encryption_method) are visible on the user profile, which means you can query them using Management API.

| Name                       | Type      | Description                                      | Unique  | Required  |
|----------------------------|-----------|--------------------------------------------------|--------|-----------|
| id                         | String    | Unique identifier                                |   ✅   |    ✅    |
| username                   | String    | Username for sign-in                             |   ✅   |    ❌    |
| primary_email              | String    | Primary email                                    |   ✅   |    ❌    |
| primary_phone              | String    | Primary phone number                             |   ✅   |    ❌    |
| name                       | String    | Full name                                        |   ❌   |    ❌    |
| avatar                     | String    | URL pointing to user's avatar image              |   ❌   |    ❌    |
| password_encrypted         | String    | Encrypted password                               |   ❌   |    ❌    |
| password_encryption_method | String    | Password encryption method                       |   ❌   |    ❌    |
| application_id             | String    | Application ID that the user first registered    |   ❌   |    ✅    |
| custom_data                | Object    | Additional info in customizable properties       |   ❌   |    ✅    |
| identities                 | Object    | User info retrieved from social sign-in          |   ❌   |    ✅    |
| last_sign_in_at            | Date time | Timestamp when the user signed in last time      |   ❌   |    ✅    |
| is_suspended               | Boolean   | User suspend mark                                |   ❌   |    ✅    |

NOTE
- Unique: Ensures the uniqueness of the values entered into a property of a database table.
- Required: Ensures that the values entered a property of a database table can NOT be NULL.

## User Profile
Each user has a profile containing all user information.

It consists of the following types of data:
- Basic data: is the basic info from the user profile. It stores all other user's properties except for identities and custom_data, such as user id, username, email, phone number, and when the user last signed in.
- Custom data: stores additional user info not listed in the pre-defined user properties, such as user-preferred color and language.
- Social identities: stores the user info retrieved from social sign-in (i.e., sign-in with a social connector), such as Facebook, GitHub, and WeChat.

Here is a sample of a user's data which is retrieved from a sign-in to Facebook:

```
{
  "id": "iHXPuSb9eMzt",
  "username": null,
  "primaryEmail": null,
  "primaryPhone": null,
  "name": "John Joe",
  "avatar": "https://example.com/avatar.png",
  "customData": {
    "preferences": {
      "language": "en",
      "color": "#f236c9"
    }
  },
  "identities": {
    "facebook": {
      "userId": "106077000000000",
      "details": {
        "id": "106077000000000",
        "name": "John Joe",
        "email": "johnjoe@berani.id",
        "avatar": "https://example.com/avatar.png"
      }
    }
  },
  "lastSignInAt": 1655799453171,
  "applicationId": "berani_app"
}
```

## Basic data
Let's walk through all properties in of user's basic data.

### id
id is a unique auto-generated key to identify the user in our system.

### username
username is used for sign-in with username and password.

Its value is from the username that the user first registered with. It may be null. Its non-null value should be no longer than 128 characters, only contain letters, numbers, and underscores (_), and NOT start with a number.

### primary_email
primary_email is the user's email address, used for sign-in with the email and passcode.

Its value is usually from the email address that the user first registered with. It may be null. Its max length is 128.

### primary_phone
primary_phone is the user's phone number, used for sign-in with the phone number and passcode from SMS.

Its value is usually from the phone number that the user first registered with. It may be null. Its non-null value should contain numbers prefixed with the country calling code (excluding the plus sign +).

### name
name is the user's full name. Its max length is 128.

### avatar
avatar is the URL pointing to the user's avatar image. Its max length is 2048.

If the user registers with a social connector like Facebook and WeChat, its value may be retrieved from the social user info.

### application_id
The value of application_id is from the application the user first signed in to. It may be null.

### last_signed_in_at
last_signed_in_at is the timestamp with the timezone when the user signed in last time.

### password_encrypted
password_encrypted is used to store the user's encrypted password.

Its value is from the password that the user first registered with. It may be null. If its value is non-null, its original content before encryption should be at least six characters.

### password_encryption_method
password_encryption_method is used to encrypt the user's password. Its value is initialized when the user registers with the username and password. It may be null.

For example we uses Argon2's implementation node-argon2 as the encryption method by default; see the reference for details if you're interested.

Sample a password_encrypted and password_encryption_method from a user whose password is 123456:

```
{
  "password_encryption_method": "Argon2i",
  "password_encrypted": "$argon2i$v=19$m=4096,t=10,p=1$aZzrqpSX45DOo+9uEW6XVw$O4MdirF0mtuWWWz68eyNAt2u1FzzV3m3g00oIxmEr0U"
}
```

### is_suspended
is_suspended is a boolean value that indicates whether a user is suspended or not. The value can be managed by calling the Management API or using Admin Console.

Once a user is suspended the pre-granted refresh tokens will be revoked immediately and the user won't be able to get authenticated by our system anymore.

## Custom Data

Custom data stores additional user info not listed in the pre-defined user properties.

You can use custom_data to do the following things:

- Record whether specific actions have been done by the user, such as having seen the welcome page.
- Store application-specific data in the user profile, such as the user's preferred language and appearance per application.
- Maintain other arbitrary data related to the user.
Sample custom_data from an admin user in Logto:

```
{
  "adminConsolePreferences": {
    "language": "en",
    "appearanceMode": "system",
    "experienceNoticeConfirmed": true
  },
  "customDataFoo": {
    "foo": "foo"
  },
  "customDataBar": {
    "bar": "bar"
  }
}
```

Each user's custom_data is stored in an individual JSON object.

## Social identities

Social identities contains the user info retrieved from social sign-in (i.e., sign-in with a social connector). Each user's identities is stored in an individual JSON object.

The user info varies by social identity provider (i.e., social network platform), and it typically includes the following:

- Identity provider, such as "facebook", "google", or "wechat"
- User's unique identifier for this provider
- User's name
- User's verified email
- User's avatar

The user's account may be linked to multiple social identity providers via social sign-in; the corresponding user info retrieved from these providers will be stored in the identities object.

Sample identities from a user who signed in with both Facebook and WeChat:

```
{
  "facebook": {
    "userId": "5110888888888888",
    "details": {
      "id": "5110888888888888",
      "name": "John Joe",
      "email": "johnjoe@logto.io",
      "avatar": "https://example.com/avatar.png"
    }
  },
  "wechat": {
    "userId": "O8sU-6JWMMNZzuXo6-xaEjouyQZ8",
    "details": {
      "id": "O8sU-6JWMMNZzuXo6-xaEjouyQZ8",
      "name": "John Joe",
      "avatar": "https://example.com/avatar.png"
    }
  }
}
```

---
Powered by Berani Digital ID © 2024
