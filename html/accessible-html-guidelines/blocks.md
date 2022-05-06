---
cover: ../../.gitbook/assets/block.php.png
coverY: 487.27272727272725
---

# Blocks

### Resources

{% embed url="https://docs.airwptheme.com/air-blocks/block-library" %}

### Section blocks

This is an example on what structure should be used in Gutenberg Blocks.

```html
<section class="block block-example">
  <div class="container">
    <div class="cols">
      <div class="col col-text">
        <p class="block-title-pre" aria-describedby="block-title-something">Some pre-heading</p>
        
        <h2 class="block-title" id="block-title-something">
          <a href="#">Some heading - Lorem ipsum</a>
        </h2>
        
        <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
        
        <p>
          <span>Aenean ac ultrices metus.</span>
        </p>
      </div> 
      
      <div class="col col-image col-poster">
        <img src="#" alt="Dynamic title" />
      </div>
    </div>
  </div>
</section>
```

