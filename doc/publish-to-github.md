# Publishing to GitHub

## Example
1. If you haven't cloned the example git repositories follow the instructions from {doc}`library-build`

2. Switch to the [github-pub](https://github.com/bradubv/greet-app/tree/github-pub) branch of the [greet-app](https://github.com/bradubv/greet-app) repo

3. You will need to generate a Personal Access Token in GitHub.  The token just needs read:packages permissions
    - Click on your profile picture in the upper right hand corner
    - Pick Settings
    - On the left hand side click Developer settings all the way down.
    - Pick Personal access tokens
    - Pick Tokens (classic)
    - Click Generate new token and pick Generate new token (classic)
    - Give your token a name, set the expiration period and click read:packages under Select scopes
    - Scroll down and click Generate token
    - You only have this chance to copy the token.  After this you will no longer be able to see it.

4. Open a PowerShell terminal (CTRL + `) and set up environment variables
```
$env:GITHUB_ACTOR = "your_github_login"
$env:GITHUB_TOKEN = "your_github_token"
``` 

5. You should now be able to clean the project
```
.\gradlew clean
```

6. Run it
```
.\gradlew run
```

7. Take a look at the commits that moved the location of the repository on the [library](https://github.com/bradubv/greet-lib/commit/0d989e33b6cf0d0a3436f4000972c520e65ec7f8) and the [application](https://github.com/bradubv/greet-app/commit/765a2551f283795b4cdb04f4a23c5b7984a3d759).

## TODO
1. Figure out why build.gradle is not loading the variables from gradle.properties