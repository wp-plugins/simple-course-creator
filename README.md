Simple Course Creator
=====================

View it on WordPress: (http://wordpress.org/plugins/simple-course-creator/)

Simple Course Creator is designed to easily link posts together in a series and output that series list in the content of each included post.

#### Add-ons

* [Simple Course Creator Customizer](https://github.com/sdavis2702/simple-course-creator-customizer)
* [Simple Course Creator Post Meta](https://github.com/sdavis2702/simple-course-creator-post-meta)
* [Simple Course Creator Front Display](https://github.com/sdavis2702/simple-course-creator-front-display)

### How It Works
---

Once activated, a new taxonomy is added to your Posts menu called "Courses." Courses are created just like categories and tags.

When creating a new course, it's important to give the course a description as well as a title, which is a new field added by this plugin.

![Create New Course](http://seandavis.co/wp-content/uploads/2014/02/Screen-Shot-2014-02-24-at-2.44.16-PM.png)

Now with at least one course created, you have the ability to select which course a post belongs to from the edit post screen.

![Select Course](http://seandavis.co/wp-content/uploads/2014/02/Screen-Shot-2014-02-24-at-2.47.48-PM.png)

Once a course is selected and saved, a course listing will appear in the content of said post as long as it's not the only post in a course.

The course listing will display as a container that shows nothing but the course title and the course description, which is what you filled out when creating a new course.

The series of posts will be hidden until you click a subtle link for displaying them, at which point the container will gracefully expand to reveal all posts in said course. They will all be linked except for the current post.

![Course Collapsed](http://buildwpyourself.com/wp-content/uploads/2014/03/course-collapsed.png)

![Course Expanded](http://buildwpyourself.com/wp-content/uploads/2014/03/course-expanded.png)

Styles are kept to a minimum so theme styles are inherited as much as possible.

### Simple Course Creator Settings
---

Simple Course Creator comes with a few very simple options.

Choose to display your course containers above post content, below post content, both above and below post content, or do not display it at all while still preserving the course configuration.

You may also choose your course list style type. They can be displayed as a numbered list, a bulleted list, or a list with no list indicator at all... simply stacked like paragraphs.

![Simple Course Creator Settings](http://buildwpyourself.com/wp-content/uploads/2014/03/scc-settings.png)

Expect more options in the future.

### Theme Overrides
---

#### WordPress Hooks & Filters

The simplest way to edit your course output is with hooks and filters in your active theme's functions file. SCC comes with built-in hooks littered throughout the output as well as a filter for the course toggle.

Here's a list of all the hook names:

* scc_before_container
* scc_container_top
* scc_below_title
* scc_below_description
* scc_before_toggle
* scc_after_toggle
* scc_above_list
* scc_before_list_item
* scc_after_list_item
* scc_below_list
* scc_container_bottom
* scc_after_container

To use any of these hooks, create your own custom function and use WordPress' `add_action()` function to call your function with the specific hook location. Here's an example.

``` php
function function_name() { ?>
    -- custom --
<?php }
add_action( 'scc_container_top', 'function_name' );
```
	
Pasting that PHP into your active theme's functions file will output "-- custom --" just inside every course container box.

To edit the "full course" toggle link, use the built-in filter `course_toggle` like so.

``` php
function function_name_filter( $toggle ) {
	$toggle = str_replace( 'full course', 'complete series', $toggle );
	return $toggle;
}
add_filter( 'course_toggle', 'function_name_filter' );
```

With a little CSS usage in your own theme stylesheet, the plugin settings, and the above actions, you can customize SCC however you'd like.

Or...

#### Active Theme File Overrides

You are more than welcome to override the basic default styles, behavior, or HTML template responsible for displaying the course container.

If you only want to edit a few CSS styles, you're better off using your own theme's stylesheet and simply writing stronger CSS.

If you would like to override the actual CSS file, JavaScript file, or HTML template for displaying the course container, you can easily do so by creating a folder in the root of your theme called `scc_templates` and copying any of the files you'd like from the plugin's `includes/scc_templates` folder into your new theme folder. 

Your theme files will now completely override the plugin files.

Be sure to copy these files and not simply create new, empty ones. Even if they're empty, they'll still override.

### Bugs and Contributions
---

If you notice any mistakes, feel free to fork the repo and submit a pull request with your corrections. The same is true of any features you feel should be added or changes that can be made. 

### License
---

This plugin, like WordPress, is licensed under the GPL. Do what you want with it. I seriously don't care. 

### Developer
---

I'm Sean. I created the [Volatyl Framework](http://volatylthemes.com) for WordPress. I like to do most of my WordPress stuff on [Build WordPress Yourself](http://buildwpyourself.com/). I also write stuff on my [personal site](http://seandavis.co) and [SDavis Media](http://sdavismedia.com). Follow me on the [Twitter](http://sdvs.me/twitter) machine.

Meanwhile, tell me... is this plugin useful to you? If so, consider buying me a box of "Tazo: Awake - English Breakfast Black Tea." I need ALL the energiez. Thanks. [Donate Black Tea](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=52HQDSEUA542S)
