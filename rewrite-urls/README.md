If the AllowOverride directive is set to anything other than None, you can specify certain configuration options at the directory level, through the .htaccess file. This file is most often used for rewriting URLs, authenticating users in a protected directory, or specifying error documents for a site.

The directives contained within the .htaccess file take precedence over directives in the httpd.conf configuration file, and apply to all subdirectories contained within.

Here is an example of a .htaccess file that configures basic authentication, as well as setting up clean URLs that redirect everything to a parameter or index.php.