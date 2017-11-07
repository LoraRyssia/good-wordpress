# WP Query

*   [Loops](https://github.com/LoraRyssia/good-wordpress/tree/master/custom-post#loops)
*   [Methods and Properties](https://github.com/LoraRyssia/good-wordpress/tree/master/custom-post#search)


## Loops

### Standard Loop

``` bash
<?php
 
// The Query
$the_query = new WP_Query( $args );
 
// The Loop
if ( $the_query->have_posts() ) {
    echo '<ul>';
    while ( $the_query->have_posts() ) {
        $the_query->the_post();
        echo '<li>' . get_the_title() . '</li>';
    }
    echo '</ul>';
} else {
    // no posts found
}
/* Restore original Post Data */
wp_reset_postdata();
```

### Standard Loop (Alternate)

``` bash
<?php 
// the query
$the_query = new WP_Query( $args ); ?>
 
<?php if ( $the_query->have_posts() ) : ?>
 
    <!-- pagination here -->
 
    <!-- the loop -->
    <?php while ( $the_query->have_posts() ) : $the_query->the_post(); ?>
        <h2><?php the_title(); ?></h2>
    <?php endwhile; ?>
    <!-- end of the loop -->
 
    <!-- pagination here -->
 
    <?php wp_reset_postdata(); ?>
 
<?php else : ?>
    <p><?php _e( 'Sorry, no posts matched your criteria.' ); ?></p>
<?php endif; ?>
```

## Methods and Properties

This is the formal documentation of WP_Query. You shouldn’t alter the properties directly, but instead use the methods to interact with them.

### Properties

`$query`
Holds the query string that was passed to the $wp_query object by WP class.

`$query_vars`
An associative array containing the dissected $query: an array of the query variables and their respective values.

`$queried_object`
Applicable if the request is a category, author, permalink or Page. Holds information on the requested category, author, post or Page.

`$queried_object_id`
If the request is a category, author, permalink or post / page, holds the corresponding ID.

`$posts`
Gets filled with the requested posts from the database.

$post_count
The number of posts being displayed.

$found_posts
The total number of posts found matching the current query parameters

$max_num_pages
The total number of pages. Is the result of $found_posts / $posts_per_page

$current_post
(available during The Loop) Index of the post currently being displayed.
$post
(available during The Loop) The post currently being displayed.
$is_single, $is_page, $is_archive, $is_preview, $is_date, $is_year, $is_month, $is_time, $is_author, $is_category, $is_tag, $is_tax, $is_search, $is_feed, $is_comment_feed, $is_trackback, $is_home, $is_404, $is_comments_popup, $is_admin, $is_attachment, $is_singular, $is_robots, $is_posts_page, $is_paged
Booleans dictating what type of request this is. For example, the first three represent ‘is it a permalink?’, ‘is it a Page?’, ‘is it any type of archive page?’, respectively.

``` bash
<form class="search" action="<?php echo home_url( '/' ); ?>">
    <input type="search" name="s" placeholder="Search&hellip;">
    <input type="submit" value="Search">
    <input type="hidden" name="post_type" value="custom-post-type">
</form>
```






