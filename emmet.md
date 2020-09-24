# Emmet

## HTML Emmet

### !! produces the following HTML

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!-- Bootstrap -->
    <link
      rel="stylesheet"
      href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css"
      integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk"
      crossorigin="anonymous"
    />
    <!-- JS, Popper.js, and jQuery -->
    <script
      src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
      integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj"
      crossorigin="anonymous"
    ></script>
    <script
      src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
      integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo"
      crossorigin="anonymous"
    ></script>
    <script
      src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"
      integrity="sha384-OgVRvuATP1z7JjHLkuOU7Xw704+h835Lr+6QL9UvYjZE3Ipu6Tp75j7Bh/kR0JKI"
      crossorigin="anonymous"
    ></script>
    <!-- My CSS Styles -->
    <link rel="stylesheet" type="text/css" href="styles.css">
    <title>Document</title>
  </head>
  <body>

  </body>
</html>
```

### div#IdTag.ClassName produces

```HTML
<div id="IdTag" class="ClassName"></div>
```

### .row>.col-md-4>.card>h4.card-header produces

```HTML
<div class="row">
  <div class="col-md-4">
    <div class="card">
      <h4 class="card-header"></h4>
    </div>
  </div>
</div>

```

### .nav>ul>li.menu-item\$\*5 produces

```HTML
<div class="nav">
  <ul>
    <li class="menu-item1"></li>
    <li class="menu-item2"></li>
    <li class="menu-item3"></li>
    <li class="menu-item4"></li>
    <li class="menu-item5"></li>
  </ul>
</div>
```

### section>(header>nav.nav>ul>li.menu-item${menu-item$}*5)(left>left-section.left-section)(right>right-section.right-section)(footer) produces

```HTML
<section>
  <header>
    <nav>
      <ul class="nav nav-pills nav-fill">
        <li class="menu-item1">menu-item1</li>
        <li class="menu-item2">menu-item2</li>
        <li class="menu-item3">menu-item3</li>
        <li class="menu-item4">menu-item4</li>
        <li class="menu-item5">menu-item5</li>
      </ul>
    </nav>
  </header>
  <left>
    <left-section class="left-section"></left-section>
  </left>
  <right>
    <right-section class="right-section"></right-section>
  </right>
  <footer></footer>
</section>
```

### header.container>div.row>.col-md-4>h1.site-title>a[href="index.html"]{Site Name}^^.col-md-8>ul.nav.justify-content-end>li.nav-item>a.nav-link[href="home.html"]{Home}^li.nav-item>a.nav-link[href="about.html"]{About}^li.nav-item>a.nav-link[href="contact.html"]{Contact} produces

```HTML
<header class="container">
  <div class="row">
    <div class="col-md-4">
      <h1 class="site-title"><a href="index.html">Site Name</a></h1>
    </div>
    <div class="col-md-8">
      <ul class="nav justify-content-end">
        <li class="nav-item"><a href="home.html" class="nav-link">Home</a></li>
        <li class="nav-item"><a href="about.html" class="nav-link">About</a></li>
        <li class="nav-item"><a href="contact.html" class="nav-link">Contact</a></li>
      </ul>
    </div>
  </div>
</header>
```

### main.container>.row>.primary.col-md-8>article>h1.article-title{Article Title}+p*3>lorem22^^^aside.col-md-4#sidebar>.card>h2.card-header{about-us}+.card-body>p>lorem22 produces

```HTML
    <main class="container">
      <div class="row">
        <div class="primary col-md-8">
          <article>
            <h1 class="article-title">Article Title</h1>
            <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Ea, magnam nihil omnis tenetur quas explicabo mollitia. Perspiciatis necessitatibus cumque officia sit odit.</p>
            <p>Repudiandae, necessitatibus adipisci. Iste quidem modi atque magni amet quisquam porro, nihil id cumque aliquam tenetur fugit ipsa eligendi esse exercitationem doloribus.</p>
            <p>Velit consequatur iste nam delectus maiores id odit optio ratione repellat nobis tempore accusamus neque corrupti amet itaque repudiandae praesentium, quo aliquid?</p>
          </article>
        </div>
        <aside class="col-md-4" id="sidebar">
          <div class="card">
            <h2 class="card-header">about-us</h2>
            <div class="card-body">
              <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Vitae unde ratione laborum doloribus odit esse tempore natus fuga. Ipsum accusamus ratione quos.</p>
            </div>
          </div>
        </aside>
      </div>
    </main>
```

### footer.container>.row>.col-md-4*3>.card>h4.card-header{card header}+.card-body>p>lorem22 produces

```HTML
    <footer class="container">
      <div class="row">
        <div class="col-md-4">
          <div class="card">
            <h4 class="card-header">card header</h4>
            <div class="card-body">
              <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio odio ea soluta dicta. Molestiae, atque facere! Sapiente exercitationem iste voluptas accusamus aspernatur?</p>
            </div>
          </div>
        </div>
        <div class="col-md-4">
          <div class="card">
            <h4 class="card-header">card header</h4>
            <div class="card-body">
              <p>Iusto voluptate dolorum autem, est fuga perspiciatis voluptatibus, corporis pariatur sapiente laborum a accusantium soluta quidem rem nostrum impedit quo officia minima.</p>
            </div>
          </div>
        </div>
        <div class="col-md-4">
          <div class="card">
            <h4 class="card-header">card header</h4>
            <div class="card-body">
              <p>Laboriosam commodi quidem sit ipsa? Iure facere accusantium et natus numquam architecto! Molestiae asperiores autem suscipit magnam. Soluta fuga quisquam quidem dolore?</p>
            </div>
          </div>
        </div>
      </div>
    </footer>
```
