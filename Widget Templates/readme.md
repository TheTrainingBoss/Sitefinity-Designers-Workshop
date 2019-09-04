Widget Templates
----------------

> What if you don\'t like the way a widget is arranged or the type of
> content it contains? Widgets template allow you to tailor the layout.
>
> Accessing Widget Templates
>
> You can access widget templates from the Administration menu and from
> the edit link of the widget.
>
> The Administration menu *Design \> Widget templates* option shows the
> name of the template and where the template is used. For example, the
> *List of threads* template is applied to the Forums threads list.
> Click the *Name* link to edit the template.

![](./media/image248.png){width="5.71875in"
height="1.9819444444444445in"}

> The *Edit* link of the allows you to select a template and then edit
> it, or create an entirely new template.

![](./media/image250.png){width="3.572785433070866in" height="1.0725in"}

> 120 \| DESIGNERS
>
> Changing a Template
>
> This next walk-through assumes you already have one or more blog posts
> created. The blogs should have Tags defined.

1.  Drag a *Blog Posts* widget to a page.

2.  Click the widget *Edit* button.

3.  Click the *List Settings* link.

4.  Select the *Titles and dates* template from the drop down list

5.  Click the *Edit selected template* button.

![](./media/image251.png){width="3.64867782152231in"
height="1.381874453193351in"}

121 \| DESIGNERS

> The Edit template page displays three areas: HTML markup, a right hand
> insert menu, and the bottom of the page edits for *Template name* and
> *Name for developers*.

![](./media/image252.jpeg){width="6.515676946631671in"
height="4.0307283464566925in"}

> The HTML markup uses ASP.NET syntax and has special tags that
> reference Sitefinity data fields. The *Blogs Insert\...* menu lists
> the data that can be dropped right into your widget. To make it easier
> to use, the list is divided into *Common data* fields you\'re likely
> to use and *Other data* that lists all possible fields. The *Template
> name* is used by Sitefinity to identify the template.
>
> 122 \| DESIGNERS
>
> To add new data to the template:

1.  Place your cursor in the HTML just below the PostDate field, as
    shown in the screenshot below.

![](./media/image253.png){width="3.428472222222222in"
height="2.3354166666666667in"}

2.  From the *Blogs Insert\...* menu, click the *Tags* item. Sitefinity
    automatically creates the markup you need. Click the *Insert* button
    to place the markup at the cursor position.

![](./media/image255.png){width="4.145536964129484in"
height="2.3306244531933507in"}

123 \| DESIGNERS

3.  Click the *Save* changes button.

4.  Click the *Save* button.

5.  Now the widget lists the tags below the title and publication date.

![](./media/image256.png){width="2.2066666666666666in"
height="1.1666666666666667in"}

> Creating a New Template
>
> What happens to your changed template when a new version of Sitefinity
> is installed? The template may be overwritten by the new installation.
> The recommended approach is to create a new template that will not
> conflict with built-in templates. You can copy all the HTML from
> another template and then add any fields that you want.

1.  Click the Blog Posts widget *Edit* button.

2.  Click the *List Settings* link.

3.  Select the *Titles and dates template*, then click the *Edit
    selected template* button.

4.  Click the *Restore template to default* button. This rolls back any
    changes you have made to the original definition stored in the
    database.

![](./media/image257.png){width="3.5289162292213474in"
height="1.4495833333333332in"}

> 124 \| DESIGNERS

5.  Click the confirmation *Yes, restore the default version\...*
    button.

6.  Select all the HTML in the editing window, right-click and select
    *Copy* from the context menu.

7.  Click the *Save changes* button.

8.  Click the *Create New Template* button.

![](./media/image258.png){width="3.6034722222222224in"
height="1.0333333333333334in"}

9.  Place your cursor in the editing window and paste the HTML from the
    clipboard.

10. Enter a unique, descriptive template name.

![](./media/image260.png){width="3.738888888888889in"
height="0.7305555555555555in"}

11. Click the *Save changes* button. The new template should appear in
    the list of templates where it can be assigned or edited.

12. Select your new template from the List template drop down.

![](./media/image262.png){width="3.698611111111111in"
height="1.6583333333333334in"}

13. Click the *Edit* selected template button.

> **Note**: Why are we saving, then going back and editing? The
> right-hand menu is not populated with blog fields until after the
> save.

125 \| DESIGNERS

14. Place your cursor in the HTML just below the PostDate field.

15. From the Blogs Insert menu on the right side, open the *Other data*
    section and click the *LastModified* field. This step displays HTML
    markup that you can insert into your widget template.

![](./media/image264.png){width="4.665726159230096in"
height="2.6770833333333335in"}

16. Click the *Insert* button to paste the generated code into the HTML
    window.

17. Click the *Save changes* button.

18. Click *Save*.

19. Click the *Save* button.

20. The widget with the new template shows the modified date below the
    publication date.

![](./media/image265.png){width="2.2083333333333335in"
height="0.8770833333333333in"}

> 126 \| DESIGNERS
>
> Using Custom Fields in Widgets
>
> Custom fields for pages and content types is listed in the widget
> editor, right along with the built-in Sitefinity fields. For example,
> custom fields can be added to blog posts, using the Custom Fields for
> posts link from the right-hand menu.
>
> For example, a "More Info" field could be added to each blog post that
> contains a URL pointing to information relating to the post. The
> settings for the custom "More Info" field might look something like
> this:

![](./media/image267.png){width="4.111175634295713in"
height="2.1354166666666665in"}

127 \| DESIGNERS

> Here's an example blog post that uses the "More Info" custom field, at
> the bottom of the page:

![](./media/image268.jpeg){width="6.453805774278215in"
height="5.645833333333333in"}

> 128 \| DESIGNERS
>
> You can use the same procedure described in [[Creating a New
> Template]{.underline},](#_bookmark27) but instead of adding a
> PostDate, the new MoreInfo field shows up in the right-hand list of
> blog fields.

![](./media/image269.png){width="1.4055566491688538in"
height="2.1041666666666665in"}

> When you click the custom field, the *How to insert...* dialog pops up
> with markup to display the field as text:
>
> \<sitefinity:textfield runat=\"server\" displaymode=\"Read\"
>
> value=\'\<%\# Eval(\"MoreInfo\")%\>\' /\>
>
> We want to display this as a link so change the markup to use an HTML
> anchor \<a\> tag instead:
>
> \<a runat=\"server\" target=\"\_blank\" href=\'\<%\#
> Eval(\"MoreInfo\")%\>\'\>More Info\</a\>
>
> The rendered widget adds a new "More info" link. The URL for the link
> is defined in the custom field.

![](./media/image270.png){width="1.67332239720035in" height="0.78375in"}

129 \| DESIGNERS

> Managing Widget Templates
>
> Widget templates are managed from the *Design \> Widget Templates*
> menu option. You should be able to see your new widget in this list,
> with your login name listed in the *Owner* column. The widgets are
> grouped into *Area*. Also notice that the *Applied To* column
> indicates where the template is used. To open the widget template for
> editing, click the link in the *Name* column.

![](./media/image271.png){width="6.278472222222222in"
height="0.7722222222222223in"}

> 130 \| DESIGNERS