---
# this is an empty front matter
---
<!DOCTYPE html>
<html lang="en">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
  <meta charset="utf-8">
  <meta http-equiv="x-ua-compatible" content="ie=edge">
  <title>Kate Beavis | Software Engineer | Testing HTTP requests in Rails with VCR</title>
  <meta name="description" content="A guide to setting up the VCR gem in Rails to test HTTP requests">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <meta property="og:title" content="Testing HTTP requests in Rails with VCR">
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://katebeavis.github.io/posts/testing-http-requests-in-rails-with-vcr">
  <meta property="og:description" content="A guide to setting up the VCR gem in Rails to test HTTP requests">
  <meta property="og:site_name" content="Kate Beavis | Software Engineer">
  <meta property="og:image" content="https://katebeavis.github.io/assets/og-image.png">

  <meta name="twitter:card" content="summary">
  <meta name="twitter:url" content="https://katebeavis.github.io/posts/testing-http-requests-in-rails-with-vcr">
  <meta name="twitter:title" content="Testing HTTP requests in Rails with VCR">
  <meta name="twitter:description" content="A guide to setting up the VCR gem in Rails to test HTTP requests">
  <meta name="twitter:image" content="https://katebeavis.github.io/assets/og-image.png">

  <link rel="apple-touch-icon" href="/assets/apple-touch-icon.png">
  <link href="https://katebeavis.github.io/feed.xml" type="application/rss+xml" rel="alternate" title="Kate Beavis | Software Engineer Last 10 blog posts">

  
    <link type="text/css" rel="stylesheet" href="/assets/light.css">
  
</head>

<body>
  <main role="main">
    <div class="grid grid-centered">
      <div class="grid-cell">
        <nav class="header-nav reveal">
  <a href="/" class="header-logo" title="Kate Beavis | Software Engineer">Kate Beavis <span class="subtitle" style="color: #b3b3b3; font-size: 0.95em;">Software Engineer</span></a>
  <br>
  <div>
    
      <a href="/" style="margin-right: 1em;">Blog</a>
    
    
      <a href="/about" style="margin-right: 1em;">About me</a>
    
    
      <a href="/projects">Projects</a>
    
  </div>
  <ul class="header-links">
    
    
      <li>
        <a href="https://twitter.com/katebeavis" target="_blank" title="Twitter">
          <span class="icon icon-social-twitter"></span>
        </a>
      </li>
    
    
    
      <li>
        <a href="https://github.com/katebeavis" target="_blank" title="GitHub">
          <span class="icon icon-social-github"></span>
        </a>
      </li>
    
    
    
    
      <li>
        <a href="https://www.linkedin.com/in/kate-beavis-679a9990" target="_blank" title="LinkedIn">
          <span class="icon icon-social-linkedin"></span>
        </a>
      </li>
    
    
    
    
  </ul>
</nav>

        <article class="article reveal">
          <header class="article-header">
            <h1>Testing HTTP requests in Rails with VCR</h1>
            <p>A guide to setting up the VCR gem in Rails to test HTTP requests</p>
            <div class="article-list-footer">
              <span class="article-list-date">
                January 15, 2017
              </span>
              <span class="article-list-divider">-</span>
              <span class="article-list-minutes">
                
                
                  4 minute read
                
              </span>
              <span class="article-list-divider">-</span>
              <div class="article-list-tags">
                
                  <a href="/tag/ruby">ruby</a>
                
                  <a href="/tag/rails">rails</a>
                
                  <a href="/tag/testing">testing</a>
                
                  <a href="/tag/rspec">rspec</a>
                
              </div>
            </div>
          </header>

          <div class="article-content">
            
            <div markdown="1">
               My text with **markdown** syntax
            </div>

          </div>

          <div class="article-share">
            
            <a href="" title="Share on Twitter" onclick="window.open('https://twitter.com/home?status=Testing HTTP requests in Rails with VCR - https://katebeavis.github.io/posts/testing-http-requests-in-rails-with-vcr by @katebeavis', 'newwindow', 'width=500, height=225'); return false;">
              <span class="icon icon-social-twitter"></span>
            </a>
            <a href="" title="Share on Facebook" onclick="window.open('https://www.facebook.com/sharer/sharer.php?u=https://katebeavis.github.io/posts/testing-http-requests-in-rails-with-vcr', 'newwindow', 'width=500, height=500'); return false;">
              <span class="icon icon-social-facebook"></span>
            </a>
            <a href="" title="Share on Google+" onclick="window.open('https://plus.google.com/share?url=https://katebeavis.github.io/posts/testing-http-requests-in-rails-with-vcr', 'newwindow', 'width=550, height=400'); return false;">
              <span class="icon icon-social-googleplus"></span>
            </a>
          </div>

          
            <div id="disqus_thread" class="article-comments"></div>
            <script>
              (function() {
                  var d = document, s = d.createElement('script');
                  s.src = '//katebeavis-github-io.disqus.com/embed.js';
                  s.setAttribute('data-timestamp', +new Date());
                  (d.head || d.body).appendChild(s);
              })();
            </script>
            <noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a>
</noscript>
          
        </article>
        <footer class="footer reveal">
  <p>
    Blog template for Jekyll built by
    <a href="https://github.com/nielsenramon/chalk" title="Nielsen Ramon">Nielsen Ramon</a>
  </p>
</footer>

      </div>
    </div>
  </main>
  <script type="text/javascript" src="/assets/vendor.js"></script>
<script type="text/javascript" src="/assets/application.js"></script>

<script src="https://ajax.googleapis.com/ajax/libs/webfont/1.6.16/webfont.js"></script>
<script>
  WebFont.load({
    google: {
      families: ['Cormorant Garamond:700', 'Lato:300,400,700']
    }
  });
</script>



</body>
</html>
