Themes for Legacy Web Forms based pages
----------------------------------------

Themes define a set of colors, fonts and CSS for your page templates
and widgets. To add a theme to your page template: (**This is mainly for Hybrid or Web Forms based templates**)

-   Create a directory structure

-   Add CSS, images and JavaScript

-   Register the theme

-   Apply the theme to the template

#### Create a Directory Structure

The screenshot below shows a basic directory structure that will
successfully contain themes. CarConduit is the root of the
application, App\_Themes can contain any number of themes, and Global
contains any CSS that should load automatically.

![](../media/image315.png)

#### Add CSS

Create a main.css file in the Global directory and add the styles
below. Note that you can name the CSS file anything you want, all
CSS files in the Global directory will be loaded automatically.

> .sfPublicWrapper {
>
> font-family: \"Open Sans\", sans-serif; font-size: 12px;
>
> margin: 20px auto; width: 800px;
>
> }
>
> .Header {
>
> text-align: right;
>
> }
>
> .Footer {
>
> padding-top: 10px; background-color: \#ddd; border: 1px solid \#00f;
>
> }
>
#### Register the Theme

Select *Adminstration \> Settings \> Advanced \> Appearance \>
Frontend themes*. Click the *Create new* button. Enter the name of the
theme. Enter a path of the theme relative to the root of the website.
Click the *Save changes* button to finish registering the theme.

![](../media/image316.jpeg)

#### Apply the Theme

The last step is to apply the theme to the page template. In the Page
template editor, click the *Theme* button. If path structure and
configuration are correct, the new theme name should appear in the Set
Theme drop down list.

![](../media/image318.png)

After applying the theme, the styling changes reflect in the page
appearance.

Tips for Using Master Pages
---------------------------

You will need to perform some \"surgery\" to make the theme useful in
Sitefinity. Using master pages inside a Sitefinity website involves
three main pieces:

-   The master page itself: The master page file and its associated
    code-behind live in the App\_Master folder of the Visual Studio
    project.

-   The theme contains style related files, i.e. css, JavaScript and
    images.

-   The Sitefinity template is stored in the Sitefinity database. The
    template ties together the Master page and the Theme. The template
    is based on the master page and the theme is applied to the
    template.

In Visual Studio, you will need to edit the master file to work with
Sitefinity. Once the general areas are setup in the master page, use
the template in Sitefinity to further subdivide layout elements and to
add common content. Develop the layout to fit your requirements, then
create areas for customization using the ContentPlaceHolder control.

Here are some tips for performing "surgery" on the master page:
---------------------------------------------------------------

-   Remove everything from the inside of the \<head\> tag. Sitefinity
    will take care of meta tags and style sheet references for us, so
    the \<head\> tag elements are not needed. You will need the \<head\>
    tag itself, so do not remove it.

-   Add the attribute runat=\"server\" to the \<head\> tag. Sitefinity
    needs to access the head tag at the server and failing to do this
    will cause a \"yellow screen of death\" error.

-   Make sure there is only one \<form\> tag on the page, that it is
    just inside the \<body\> tag and that it has the runat="server" attribute and value.

-   Analyze the page looking for areas of the page that have hard-coded
    text. Replace areas of hard-coded text with ContentPlaceHolder
    controls. For example:

> \<div id=\"navigation\"\>
>
> \<asp:contentplaceholder id=\"Navigation\" runat=\"server\" /\>
>
> \</div\>
>
#### Note: 
Be sure to use *ContentPlaceHolder*, not *Placeholder*.

To make the template general-purpose, add ContentPlaceHolder controls
to any area of the master page you\'ll want to customize later. Try to
remove any formatting markup that might limit you in the future. When you get done replacing
various areas of the page, the master page becomes much smaller, only
consisting of structural markup. You can also remove JavaScript from
the master page because the widgets will supply script for things like
menu hover behavior.

The example below is a simplified example of a master page. Notice the
areas where the ContentPlaceHolder has been introduced.

> \<!DOCTYPE html PUBLIC \"-//W3C//DTD XHTML 1.0 Transitional//EN\"
> [\"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd](http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd)\"\>
>
> \<html xmlns=\"<http://www.w3.org/1999/xhtml>\"\>
>
> \<head runat=\"server\"\>
>
> \</head\>
>
> \<body\>
>
> \<form runat=\"server\" id=\"MyForm\"\>
>
> \<div id=\"wrapper\"\>
>
> \<div id=\"header\"\>
>
> \<a class=\"logo\" href=\"\#\"\>Site Home\</a\>
>
> \<div id=\"navContainer\"\>
>
> \<asp:**ContentPlaceHolder** ID=\"MyNavigation\" runat=\"server\" /\>
>
> \</div\>
>
> \</div\>
>
> \<div id=\"content\"\>
>
> \<asp:**ContentPlaceHolder** ID=\"MyContent\" runat=\"server\" /\>
>
> \</div\>
>
> \<div id=\"footer\"\>
>
> \<div class=\"one-fourth\"\>
>
> \<div class=\"footer-widget\"\>
>
> \<h3\>Testimonials\</h3\>
>
> \<div class=\"testimonial-widget\"\>
>
> \<asp:**ContentPlaceHolder** ID=\"MyTestimonials\" runat=\"server\"
> /\>
>
> \</div\>
>
> \</div\>
>
> \</div\>
>
> \<div class=\"one-fourth\"\>
>
> \<div class=\"footer-widget\"\>
>
> \<h3\>Recent Comments\</h3\>
>
> \<asp:**ContentPlaceHolder** ID=\"MyComments\" runat=\"server\" /\>
>
> \</div\>
>
> \</div\>
>
> \<div class=\"one-fourth\"\>
>
> \<div class=\"footer-widget\"\>
>
> \<h3\>Recent Posts\</h3\>
>
> \<asp:**ContentPlaceHolder** ID=\"MyPosts\" runat=\"server\" /\>
>
> \</div\>
>
> \</div\>
>
> \<div class=\"one-fourth last\"\>
>
> \<div class=\"footer-widget\"\>
>
> \<h3\>Categories\</h3\>
>
> \<asp:**ContentPlaceHolder** ID=\"MyCategories\" runat=\"server\" /\>
>
> \</div\>
>
> \</div\>
>
> \<br class=\"break\" /\>

> \<div id=\"footercredits\"\>
>
> \<asp:**ContentPlaceHolder** ID=\"MyCopyright\" runat=\"server\" /\>
>
> \</div\>
>
> \</div\>
>
> \</div\>
>
> \</form\>
>
> \</body\>
>
> \</html\>
>
The output for this template might end up looking like the screenshot
below. The master page ContentPlaceHolder controls supply areas for
the upper right hand side navigation menu, a content area below that
and sections for Testimonials, Recent Comments, Recent Posts and
Categories. The area at the bottom of the page is intended as a space
for the copyright notice but could hold other page footer content.

![](../media/image320.jpeg)

The titles in the footer for Testimonials, Recent Comments, etc., have
been hard-coded for this discussion. Just the same, you could swap out
all those titles with more ContentPlaceHolder controls. Later, if
Categories gets changed to Tags for example, someone without Visual
Studio experience could still change the content using Sitefinity
alone.

Once your template holds a master page and theme, you can simply drop
widgets into any page that uses the template. The screenshot below
shows a sample welcome page. To show something of interest in the
navigation menu, About Us, Blogs and News pages have been created
underneath the new Welcome page. The logo image is directly from the
master page markup, while the menu is a Navigation widget dropped into
the page. Below those two items, the Image Gallery widget displays a
list of images along with detail for one image. Below the Image
Gallery, Testimonials and Recent Comments are placed using a simple
Content block widget. Recent Posts uses a News widget and the Popular
Tags area holds a Classification \> Tags widget.

![](../media/image321.jpeg)


**Next Topic:**
[Responsive Web Design for Web Forms](./Responsive%20Design/readme.md)
