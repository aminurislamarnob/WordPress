<!--Custom Post Type Query-->
<div id="tabsJustifiedContent" class="tab-content">
  <div id="spinnerTab" style="display: none;">
      <div class="spinner-border text-primary" role="status">
          <span class="sr-only">Loading...</span>
      </div>
  </div>

  <div id="elevator" class="tab-pane fade active show col-md-10 offset-md-1">
    <div id="elevatorContent">
      <div class="row justify-content-md-center">
      <!--Work Custom Post Query Start for elevator-->
      <?php
      $paged = (get_query_var('paged')) ? get_query_var('paged') : 1;
      $works = new WP_Query(
          array(
              'posts_per_page' => 3, 
              'post_type' => 'work',
              'post_status' => 'publish',
              'work-category' => 'elevator',
              'paged' => $paged,
              )
          );
      while($works->have_posts()) : $works->the_post();
      $idd = get_the_ID();
      $work_thumbnail_url  = wp_get_attachment_url( get_post_thumbnail_id( $idd ) );
      ?>
          <div class="col-md-4">
              <div class="work-box work-item-box">
                  <div class="img_wrap">
                      <?php if( has_post_thumbnail() ): // check for feature image ?>
                      <img src="<?php echo $work_thumbnail_url; ?>" class="w-100" alt="<?php the_title(); ?>">
                      <?php else: ?>
                      <img src="<?php echo get_theme_file_uri(); ?>/assets/images/work3.png" class="w-100" alt="<?php the_title(); ?>">
                      <?php endif; ?>
                  </div>
                  <div class="text-center pt-1">
                      <p class="text_bold"><a class="text-b" href="<?php the_permalink(); ?>"><?php the_title(); ?></a></p>
                  </div>
                  <div class="arrow_top"><span></span></div>
              </div>
          </div>
      <?php 
      endwhile;

      //works ajax pagination
      $total_pages = $works->max_num_pages;

      if ($total_pages > 1){

          $current_page = max(1, get_query_var('paged'));
          ?>
          <div class="col-12 pt-5">
              <div id="workAjax">
                  <div class="post-pagination">
                      <nav class="navigation pagination">
                          <div class="nav-links">
                          <?php
                          echo paginate_links(array(
                              'base' => get_pagenum_link(1) . '%_%',
                              'format' => 'page/%#%',
                              'current' => $current_page,
                              'total' => $total_pages,
                              'prev_text'    => __('<i class="fas fa-caret-left"></i>'),
                              'next_text'    => __('<i class="fas fa-caret-right"></i>'),
                          ));
                          ?>
                          </div>
                      </nav>
                  </div>
              </div>
          </div>

      <?php    
      } 
      wp_reset_query(); ?>
      <!--Work Custom Post Query End-->
    </div>
  </div>
</div>

<!--Pagination jQuery Code-->
<script>
    jQuery(document).ready(function($) {
        
        //Works Elevator Tab Jquery Pagination
        $('#elevatorContent').on('click', '#workAjax a', function(event){
            event.preventDefault();

            var loaderHeight = $('#elevatorContent').height(); //get container height
            $('#spinnerTab, #elevator').css('height', loaderHeight+'px'); //add height on spinner container
            $('#spinnerTab').fadeIn('slow').delay(1500).hide(0); //show loader

            var link = $(this).attr('href');
            $('#elevatorContent').fadeOut(400, function(){
                $(this).load(link+ ' #elevatorContent', function(){
                    $(this).fadeIn(400, function(){

                    });
                });
            });
        });

    });
</script>
