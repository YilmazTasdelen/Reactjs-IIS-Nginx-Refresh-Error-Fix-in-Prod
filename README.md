# React-IIS-Refresh-Error-Fix
<div>
<pre>
<h2>for nginx</h2>
// add below your `location / {}`
location /map { 
 try_files $uri /index.html;
}}
</pre>
</div>

<div>
<pre>
<h2>for IIS</h2>
//Add rewrite rule or add tis to web.config  

```xml
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="React Routes" stopProcessing="true">
                    <match url=".*" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                        <add input="{REQUEST_URI}" pattern="^/(api)" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="/" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
```
</pre>
</div>
