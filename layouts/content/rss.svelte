<script>
    export let allContent;
	let allPosts = allContent.filter(content => content.type == "blog");

    let rssFeed = '<?xml version="1.0" encoding="UTF-8" ?><rss version="2.0"><channel><title>My Site Blog</title><link>https://www.mysite.com/blog</link><description>Awesome blog posts for my site</description>';
    allPosts.forEach(post => {
        rssFeed += '<item><title>' + post.fields.title + '</title>';
        rssFeed += '<link>' + post.path + '</link>';
        rssFeed += '<description>' + post.fields.body[0] + '</description>';
        rssFeed += '</item>';
    });
    rssFeed += '</channel></rss>';

</script>

<html lang="en">
    <head>
        <link rel="alternate" type="application/rss+xml" title="RSS Feed" href="rss" />
    </head>
    <body>
        {rssFeed}
    </body>
</html>