# Azure Active Directory Authentication

This is a sample application to test the authentication with Azure Active Directory directly in an angular application, using _msal_ library.

It is strongly based on this sample project [here](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/samples/msal-angular-v3-samples/angular16-sample-app).

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.1.0.

## Pre-requisites

The following pre-requisites are required to run the application.

### Azure Active Directory

- Active Azure subscription
- Active Azure Active Directory (AAD)
- Privileged access to AAD to register the application and assign permissions to it

#### App Registration

The angular application must be first registered in the Azure Active Directory to get identifiers that will then be used by the app to identify itself and get granted access.

By default, an anuglar app runs on _http://localhost:4200_ and thus I suggest to use this URL as the redirect URL when registering the application.

This process is well documented on many different websites and blogs:

- [Official Microsoft documentation](https://learn.microsoft.com/en-us/azure/active-directory/develop/tutorial-v2-angular-auth-code#register-the-application-and-record-identifiers)
- [This post](https://medium.com/bi3-technologies/azure-ad-sso-in-angular-within-5-minutes-8f96388b339b)

**Important**
Write down the identifiers (_client ID_ and _tenant ID_) and the redirect URL that were generated upon app registration.

#### Login URL

The login URL to setup in the application depends on the Azure AD setup one has.
It may vary a bit as explained on [this Microsoft's documentation page](https://learn.microsoft.com/en-us/azure/active-directory/develop/authentication-national-cloud#application-endpoints).

Although the might common probably is the single tenant scenario in which case the URL is _https://login.microsoftonline.com/your-tenant-ID-or-name_ where _your-tenant-ID-or-name_ must be replaced with your tenant ID (a GUID given when registering the app) or it's name (don't know the format, and I personally prefer the GUID one to avoid any doubts).

## Configure the application

### Environment configuration file

Create a new environment configuration file in the [environments](./src/environments/) directory for the environment you want to setup.

The following environments are predefined:

- _development_: create a file _[environment.dev.ts](./src/environments/environment.dev.ts)_
- _production_: create a file _[environment.prod.ts](./src/environments/environment.prod.ts)_

### Environment configuration

Open the created configuration file for the environement to setup and update the following keys with values:

- _ENTER_CLIENT_ID_: the _client ID_ generated when the app was registered
- _ENTER_AUTHORITY_: the _Login URL_ as explained above
- _ENTER_SCOPE_: an array of scopes, the app requests permissions for (defaults to _user.read_)
- _ENTER_URI_: the Microsoft Graph API URL the application calls to get user information

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
