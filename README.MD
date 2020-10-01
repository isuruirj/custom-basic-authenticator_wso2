# Custom Basic Authenticator

------

 This component has been tested with WSO2 IS 5.9.0.

### Steps to deploy
- Build the component by running "mvn clean install"
- Copy the jar file which can be found in target directory into <IS_HOME>/repository/components/dropins/
- To use this only for one/few service providers
  * Restart the Identity Server
  * Configure "custom-basic" in authentication steps in Local and Outbound authentication config of the
 service providers instead of "basic".
  * Open <IS_HOME>/repository/deployment/server/webapps/authenticationendpoint/login.jsp
  * Add a new variable `CUSTOM_BASIC_AUTHENTICATOR` near the `BASIC_AUTHENTICATOR` as below.
    ```
    private static final String BASIC_AUTHENTICATOR = "BasicAuthenticator";
    private static final String CUSTOM_BASIC_AUTHENTICATOR = "CustomBasicAuthenticator";
    ```
  * Update all the place which has `localAuthenticatorNames.contains(BASIC_AUTHENTICATOR)` as following.
    ```
    localAuthenticatorNames.contains(BASIC_AUTHENTICATOR) || localAuthenticatorNames.contains(CUSTOM_BASIC_AUTHENTICATOR)
    ```
