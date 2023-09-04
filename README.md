 ## Step 1
 Create argument using transient and then use it in loop
 ```
<?php
    // delete_transient( 'foo_featured_posts' );
    if ( false === ( $posts = get_transient( 'foo_featured_posts' ) ) ) {
    $args = array(
    'post_type'=>'xyz', 
    'orderby'=>'rand', 
    'posts_per_page'=>'1'
    );
    $posts=new WP_Query($args);
    // Put the results in a transient. Expire after 12 hours.
    set_transient( 'foo_featured_posts', $posts, 24 * HOUR_IN_SECONDS );
    }
?>
```
```
    if($posts->have_posts()):
      while ($posts->have_posts()) : $posts->the_post();  ?>
    <?php   endwhile; 
    wp_reset_postdata();
    endif;   ?>
```

Resource:  [Wordress Transients](https://developer.wordpress.org/apis/transients/)
