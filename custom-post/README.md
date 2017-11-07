# Custom Post

*   [Custom Post Loop](https://github.com/LoraRyssia/good-wordpress/tree/master/custom-post#Custom-Post-Loop)
*   [Search](https://github.com/LoraRyssia/good-wordpress/tree/master/custom-post#Search)


## Custom Post Loop

### WP Query
#### Standard Loop
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

#### Standard Loop (Alternate)

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

## Search

``` bash
<form class="search" action="<?php echo home_url( '/' ); ?>">
    <input type="search" name="s" placeholder="Search&hellip;">
    <input type="submit" value="Search">
    <input type="hidden" name="post_type" value="custom-post-type">
</form>
```






