Two new text boxes will appear in the Hudson Configure System page under the Additional page HTML Markup heading. Any text added to these boxes will appear on all pages Hudson generates.

Example: implementing a custom site banner

Many organizations desire (or require) a standardized banner at the top of all web pages. To implement this, first create a local-site.css stylesheet, and place it in the userContent[1] directory in your Hudson installation:

body { 
  margin-top: 50px;  /* the height of your site banner */
}

#site-banner {
  position: absolute;
  top: 0px;
  left: 0px;
  right: 0px;
  height: 50px;
  width: 100%;
}
Then, using the PageMarkup plugin, inject your CSS into the header and your site banner within a div block into the footer (the CSS will tell the browser to reposition it to the top of the page):

Header
<link rel="stylesheet" href="/hudson/userContent/local-site.css" type="text/css" />
Footer
<div id="site-banner">
   <!--  your banner code goes here -->
</div>
[1] Note: the URL to use to reference the userContent directory is dependent on the --prefix option that you specify when launching Hudson. In these examples, I am assuming --prefix=/hudson; adjust your URLs according to your local site configuration. Regardless, it is important to use an absolute URL (i.e. begins with a "/" character) when specifying content in the userContent directory.

Example: replacing the standard Hudson banner and footer

Through slightly more complex CSS, it is possible to completely replace the standard Hudson banner and merge it with your custom site banner. This example merges the Hudson search box and login link with a site header and rearranges the page footer. You can see it in action  here.

This relies on two CSS files:

 snl-banner.css
 snl-footer.css
And then, the actual header & footer HTML:

Header
  <link rel="stylesheet" href="/hudson/userContent/snl-banner.css" type="text/css" />
  <link rel="stylesheet" href="/hudson/userContent/snl-footer.css" type="text/css" />
Footer
<div id="snl-logo">
  <a href="http://www.sandia.gov/"><img src="/hudson/userContent/sandia_logo.png" alt="Sandia National Laboratories" /></a>
</div>
<div id="snl-copyright">
    ©2010 Sandia Corporation <br />
    <a href="http://www.sandia.gov/general/privacy-security/index.html">Privacy
         and Security</a> |
    <a href="https://software.sandia.gov/trac/fast/wiki/Hudson/ContactUs">Contact Us</a>
</div>
<div id="snl-banner-logo"><a href="http://www.sandia.gov"><img src="/hudson/userContent/snl-banner.gif" alt="Sandia National Laboratories"/></a></div>
<div id="snl-banner-title">Hudson Public Mirror</div>
<div id="snl-banner-background"/>