UrlRewriter - a rule-based URL Rewriter for .NET.

Copyright (c)2011 Seth Yates

Author [Seth Yates](https://github.com/sethyates/urlrewriter)

Author Stewart Rae

Version 2.1

Installation
============
1. Open your web project, or create a new one.
2. Add a reference to the Intelligencia.UrlRewriter assembly.
3. Open the web.config file.
4. Create a new one or Open your {YourRulesFileName}.config
5. Add Configuration section handler:

```XML
	<configSections>
		<section name="rewriter" requirePermission="false" type="Intelligencia.UrlRewriter.Configuration.RewriterConfigurationSectionHandler, Intelligencia.UrlRewriter" />
	</configSections>
```
  	
	This enables the URL Rewriter to read its configuration from the rewriteRules node in the
	web.config file.

6. Add UrlRewriter mapper HttpModule:

```XML
	<system.web>
		<httpModules>
			<add type="Intelligencia.UrlRewriter.RewriterHttpModule, Intelligencia.UrlRewriter" name="UrlRewriter" />
		</httpModules>
	</system.web>
```
  	
	This enables the URL Rewriter to intercept web requests and rewrite URL requests.
	
7.Add Intelligencia.UrlRewriter rules config file path to your web.config：

```XML
	<configuration>
		<rewriter file="~/App_Data/{YourRulesFileName}.config" />
	</configuration>
```
  	
8. Add some rules to your new {YourRulesFileName}.config file:

  	```XML
	<rewriter>
		<if url="/tags/(.+)" rewrite="/tagcloud.aspx?tag=$1" />
		<!-- same thing as <rewrite url="/tags/(.+)" to="/tagcloud.aspx?tag=$1" processing="stop" /> -->
	</rewriter>
  	```
  	
	The syntax of the rewriter section is very powerful.  Refer to the help file for more details
	of what is possible.  The above rule assumes you have mapped all requests to the .NET runtime.
	For more information on how to do this, see http://urlrewriter.net/index.php/using/installation/

9. Compile and test!
