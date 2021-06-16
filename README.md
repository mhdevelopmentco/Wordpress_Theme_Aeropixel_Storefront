AeroPixels Storefront - Wordpress
===================================

This is shopping site which sells Drone Components.

Project Period
----------------------
- Start: 2017.3.1
- Updated: 2017.3.6
- End: 2017.3.10

## Environment
- CMS: Wordpress
- Theme: AeroPixel 3,0, AeroPixel 4.0, Storefront
- Site Link: [aeropixels.com](https://aeropixels.com)

## Project History
### Storefront to AeroPixel 3.0
- Changed Product Category Walker widget
- Add Custom Class for Product Category Widget

````
	add_action( 'wp_footer', 'collapsify_product_cat_widget_js', 999999 );
	function collapsify_product_cat_widget_js() {
````

- Add Collapsible Product Category Widget to the Footer

````
	add_filter( 'woocommerce_product_categories_widget_args', 'change_product_category_walker' );
	function change_product_category_walker( $list_args ) {
		include_once( get_stylesheet_directory() . '/walkers/class-product-cat-list-walker.php' );
		$list_args['walker'] = new Custom_Product_Cat_List_Walker;

		return $list_args;
	}
 ````

- Add Custom Css via functions.php file
````
	add_action( 'wp_head', 'collapsify_product_cat_widget_css', 999999 );
	function collapsify_product_cat_widget_css() {
 		?>
 			<style>
 			....
 			</style>
 		<? }
````

- Replaced origin Footer Credit with Custom Credit
````
	add_action( 'init', 'custom_remove_footer_credit', 10 );
	function custom_remove_footer_credit () {
	    remove_action( 'storefront_footer', 'storefront_credit', 20 );
	    add_action( 'storefront_footer', 'custom_storefront_credit', 20 );
	} 
	function custom_storefront_credit() {
		?>
		<div class="site-info">
			&copy; <?php echo get_bloginfo( 'name' ) . ' ' . get_the_date( 'Y' ); ?>
		</div><!-- .site-info -->
		<?php
````

### Storefront to AeroPixel 4.0
- Updated Home page template
````
	<div id="primary" class="content-area">
		<main id="main" class="site-main" role="main">
			<?php
			/**
			 * Functions hooked in to homepage action
			 *
			 * @hooked storefront_homepage_content      - 10
			 * @hooked storefront_product_categories    - 20
			 * @hooked storefront_recent_products       - 30
			 * @hooked storefront_featured_products     - 40
			 * @hooked storefront_popular_products      - 50
			 * @hooked storefront_on_sale_products      - 60
			 * @hooked storefront_best_selling_products - 70
			 */
			do_action( 'homepage' ); ?>
		</main><!-- #main -->
	</div><!-- #primary -->
````
