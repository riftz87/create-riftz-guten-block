# create-riftz-guten-block
A boilerplate for creating a WordPress Gutenberg block  

# Usage
Change directory to your destination folder

Ex.
```
cd my-blocks
```

Run npx command
```
npx create-riftz-guten-block my-block
```
where "my-block" is the name of your block

Open index.js from src folder and change the value of namespace to your own name
```javascript
const namespace = 'riftz/my-block';
```

To start development run the following command
```
npm start
```

To build the block run the following command
```
npm run build
```

To add block to Gutenberg, copy and modify the following code to one of your initialization files such as functions.php
```php
function add_my_block_to_gutenberg() {
  $blocks_path = get_template_directory() . '/my-blocks';
  $name = 'my-block';
  $block_assets = require $blocks_path . '/' . $name . '/build/index.asset.php';
  wp_register_script( $name . '-block-js', get_template_directory_uri() . '/my-blocks/' . $name . '/build/index.js', $block_assets['dependencies'] );
  wp_register_style( $name . '-editor-css', get_template_directory_uri() . '/my-blocks/' . $name . '/build/index.css', array() );
  wp_register_style( $name . '-style-css', get_template_directory_uri() . '/my-blocks/' . $name . '/build/style-index.css', array() );
  register_block_type( 
    'riftz/' . $name, 
    array(
      'editor_script' => $name . '-block-js',
      'editor_style' => $name . '-editor-css',
      'style' => $name . '-style-css'
    ) 
  );
}
add_action( 'init', 'add_my_block_to_gutenberg' );
```

# Donations
If this helps you in your projects and think is worth paying for, I am gladly accepting kind donations. Thank you.
[![paypal](https://www.paypalobjects.com/en_US/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/donate?hosted_button_id=UW2BMEKKV27CL)
