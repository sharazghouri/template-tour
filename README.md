# Template Tour

## Description

Templates are the WordPress theme files used to render website pages. Getting acquainted with templates is an important step in learning to build themes for WordPress. This walkthrough will explain what templates are and introduce you to commonly used templates and template tags so you can edit and make your own templates.

## <span style="color: #000000">Objectives</span>

<span style="color: #000000">At the end of this lesson, you will be able to:</span>

*   <span style="color: #000000">Understand how the template renders a page and the importance of the WordPress Loop.</span>
*   <span style="color: #000000">Make and understand basic changes such as adding comments, showing text, and moving elements within the template.</span>
*   <span style="color: #000000">Understand the role of the template in theme design.</span>

## Prerequisite Skills

You will be better equipped to work through this lesson if you have experience in and familiarity with:

*   Basic knowledge of HTML/CSS
*   Understanding of how folders and files are structured
*   Ability to edit files with a text editor

## Assets

*   [Twenty Thirteen Theme](http://wordpress.org/themes/twentythirteen "Twenty Thirteen Theme")

## Screening Questions

*   Do you have at least a basic knowledge of HTML/CSS?
*   Do you feel comfortable using a text editor to edit code?
*   Will you have a locally or remotely hosted WordPress site to use during class?

## Teacher Notes

*   **Time Estimate:** 15 minutes
*   It is easiest for students to work on a locally installed copy of WordPress. Set some time aside before class to assist students with installing WordPress locally if they need it. For more information on how to install WordPress locally, please visit our [Teacher Resources page](http://make.wordpress.org/training/teacher-resources/).
*   The preferred answer to all the screening questions is “yes.” Participants who reply “no” to all the questions may not be ready for this lesson.

## Hands-on Walkthrough

### Introduction: What are Templates?

Today you are going to learn about WordPress templates. In WordPress a template is a PHP file that controls how your website’s content will be displayed in a web browser. Templates are the building block of your WordPress site. These files draw information like page or post title, content, custom fields, etc. from your WordPress database or other WordPress files and generate the HTML code on the “fly,” or dynamically. A template can control an entire page or just a section of a page and can have a high level of customization or be extremely simple. Depending on the theme you are using, or are developing, you can define as many or few templates as you need. Getting acquanited with templates is an important step in learning to build themes for WordPress.

* * *

### Templates in Twenty Thirteen

[![twentythirteen](http://make.wordpress.org/training/files/2013/10/twentythirteen.png)](http://make.wordpress.org/training/files/2013/10/twentythirteen.png)

* * *

### Features Commonly Found in WordPress Templates

*   Template Tags: code that instructs WordPress to "do" or "get" something.
*   The Loop: to gather information from the database (posts, pages, categories, etc.).

* * *

### A Tour of page.php in Twenty Thirteen

Let’s break down the parts of the page.php template in the Twenty Thirteen theme. It starts with

<pre><?php</pre>

which identifies this as a PHP file so the browser knows how to process it. Next there is a block of comments.

<pre>/**
 * The template for displaying all pages
 *
 * This is the template that displays all pages by default.
 * Please note that this is the WordPress construct of pages and that
 * other 'pages' on your WordPress site will use a different template.
 *
 * @package WordPress
 * @subpackage Twenty_Thirteen
 * @since Twenty Thirteen 1.0
 */</pre>

Comments are usually included at the top of a template file to describe it’s specific function. Right after the comments is the first template tag

<pre>get_header(); ?></pre>

It tells WordPress to insert all the information from the template file header.php at that point. Note that the opening PHP tag "<?php" was above the comments section. Because they're comments, it's like they don't exist when it comes to running the code. It the same as if the template tag was written

<pre><?php get_header(); ?></pre>

Listed next in this template file is some HTML. Usually the reason to create a template file is because you need a specific way to display content, which is tied to how the HTML is written and arranged. The HTML included in this template starts withand it <span style="color: #000000">determines</span> how the content of this specific template will be displayed. Next is a very important part of the template file - The Loop<span style="color: #000000">is</span> the core of how WordPress works. The WordPress Loop is another topic in itself but can be described as PHP code that displays WordPress database information, like a blog post title or content. It basically says "while there are posts available, then use those posts" for whatever the code does next.After that comes a few lines of HTML.

<pre>

<article>" >

<header class="entry-header"></header>

</article>

</pre>

<header class="entry-header"></header>

Then the file asks if the post has a Featured Image (<span style="color: #000000">such as a</span> thumbnail image) associated with it, and,<span style="color: #000000"> if so, displays that image.</span>

<pre class="entry-thumbnail">
<?php endif; ?></pre>

Next the file displays the post title. That's the last of the header information so the header is closed.

<pre><h1 class="entry-title"><?php the_title(); ?></h1>
 </header><!-- .entry-header --></pre>

Then the file displays the post content.The the template deals with how to display pages of content if there are many posts available. In the Settings > Reading menu on the left-hand side, there is a spot to determine how many posts should be shown on a page. If that number is exceeded, then this code kicks in and displays pagination links to view additional content.

<pre>  '

<div class="page-links"><span class="page-links-title">' 
    . __( 'Pages:', 'twentythirteen' ) . '</span>', 'after' => '</div>

', 
    'link_before' => '<span>', 'link_after' => '</span>' ) ); ?>
 </div><!-- .entry-content --></pre>

After that there are a few housekeeping items such as a link on the front-end that allows people who are logged in to click on a link to edit the page.

<pre><footer class="entry-meta">
 <?php edit_post_link( __( 'Edit', 'twentythirteen' ), '<span class="edit-link">', '</span>' ); ?></pre>

The tags that were opened at the beginning of the file need to be closed since this is the end of that type of data.

<pre> </footer><!-- .entry-meta -->
</article><!-- #post --></pre>

If there are comments, they should appear here. This template tag calls in the comments.php file and displays its code and output here.

<pre><?php comments_template(); ?></pre>

All this has been done as long as there are posts available. Remember the `while ( have_posts() ) : the_post();` statement earlier that opened The Loop? Now is the time to close The Loop.

<pre><?php endwhile; ?></pre>

Next the HTML tags that are open need to be closed as the browser continues to read the page.php template. It is important to close the HTML tags after closing The Loop.

<pre>  </div><!-- #content -->
</div><!-- #primary --></pre>

Finally, two more template tags are included which get the code and output from the sidebar.php and footer.php files respectively.

<pre><?php get_sidebar(); ?>
<?php get_footer(); ?></pre>

That's it! That's how a page template is created in WordPress. They are the files, along with their corresponding CSS files, that determine how your site will look. [![TwentyThirteen page.php code](https://make.wordpress.org/training/files/2014/10/twentythirteen-page-php-1024x757.png)](https://make.wordpress.org/training/files/2014/10/twentythirteen-page-php.png)

* * *

## Exercises

**Exercise Name**

*   Add a comment to the template file. Make sure it DOESN'T display on the front end.
*   Add some text to the template file. Makes sure it DOES display on the front end.
*   Move a the footer section above the content section. See how it is displayed now on the front end.

## Quiz

**WordPress template files are written entirely in**

1.  PHP
2.  HMTL
3.  CSS
4.  JavaScript
5.  All of the above

**Answer:** Correct Answer = 5\. All of the above
