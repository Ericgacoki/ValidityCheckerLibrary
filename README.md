[![Release](https://jitpack.io/v/User/Repo.svg)]
(https://jitpack.io/Ericgacoki/ValidityCheckerLibrary)

## Wtf is this?
---

Validity Checker is a library that simply evaluates the correctness of `emails` and `passwords`.

### A valid email must:

- Consist of a prefix and an email domain
- Follow the format as described by Android's email pattern matcher
    - The domain appears on the right side of the `@` symbol while the prefix appears on the left.

### A valid password must:

- Contain at LEAST
    - 8 to 15 characters
    - One uppercase letter(A-Z)
    - One lowercase letter(a-z)
    - One special character
    - one numerical digit(0-9)

## Usage
---

Just like any other library, ValidityChecker requires a few dependencies:

- Step 1. Add the JitPack maven repository

```gradle
allprojects {
    repositories {
        mavenCentral()
        maven { url "https://jitpack.io" }
    }
}
```

- Step 2. Add the actual library dependency

```gradle
dendencies {
	implementation 'com.github.Ericgacoki:ValidityCheckerLibrary:1.0.1'
	
	// Always use the latest version
}
```

- Step 3. Import the following

```kotlin
import com.ericdev.validitychecker.ValidityChecker
import com.ericdev.validitychecker.ValidityChecker.Valid
import com.ericdev.validitychecker.ValidityChecker.InValid
```

- Step 4. Use `isValidEmail()` to validate emails

This functions accepts one parameter of type `String` and returns `Valid` or `InValid`.

In case the argument is invalid, a reason for the first caught unmet condition is given as the error
message.

```kotlin
val email = "example@gmail.com" // you should get this from the UI
if (isValidEmail(email) is Valid) {
    // proceed
} else {
    // now that the email is invalid, we can get the error message as below
    val errorMessage = isValidEmail(email).message
}
```

- Step 5. Use `isValidPassword()` to check password's validity

Just like with emails, this method requires only one `String` argument and returns `Valid`
or `InValid`.

```kotlin
val password = "#123Testing" // you should get this from the UI
if (isValidPassword(password) is Valid) {
    // proceed
} else {
    // now that the password is invalid, we can get the error message as below
    val errorMessage = isValidPassword(password).message
}
```

`NOTE:

In cases where a password needs to be compared alongside another one for confirmation, you have to
check that as shown below:

```kotlin
val password = "..."
val confirmPassword = "..."

if (isValidPassword(password) is Valid &&
    password == confirmPassword
) {

}
```

`

That's all for now. Issues and PRs are very much welcome 😋

Resources
---

- [Documentation]("https://jitpack.io/")
- [How to Create and Publish your own Android Library]("https://www.section.io/engineering-education/how-to-create-and-publish-your-own-android-library/")
  by @JoelKanyi