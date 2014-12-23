When we enable Single-Sign-On Across Different WSO2 Products we get a default SAML SSO redirect page.

Currently we cannot customize this code directly.

Therefore, I have written a new osgi component registering a filter which redirects URL requests for the default "redirect_ajaxprocessor.jsp" to a custom jsp. With this approach I was able to change the SSO redirect "Loading WSO2 StratosLive..." to "Redirecting to SSO Login..." using this custom jsp. You can do desired customizations to this SSO redirect page using a custom ('/org.wso2.carbon.sso.redirector.custom.ui/src/main/resources/web/stratos-auth-custom/redirect_ajaxprocessor.jsp') by implementing a custom component.
 
You can checkout sample code (valid for wso2 products in carbon 4.2.0)of the above mentioned component from this git repo.

After building '/org.wso2.carbon.sso.redirector.custom.ui' component, copy the .jar into CARBON_HOME/repository/components/dropins. Restart the server.

You have to do this for every WSO2 product in the cluster. 
