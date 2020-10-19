---
layout: default
---

<div id="posts"></div>

<a class="more-button" href="https://www.instagram.com/odermalso/"><i class="ri-instagram-line"></i></a>


<script>
    const postContainer = document.querySelector("#posts");

    function getPostHTML(post) {
        post = post.node;
        const url = "https://instagram.com/p/" + post.shortcode;
        const image_url = post.display_url;
        const timestamp = new Date(post.taken_at_timestamp * 1000).toDateString();
        console.log(timestamp);
        const description = post.edge_media_to_caption.edges[0].node.text;

        return `
            <section class="post-container">
                <a href="${ url }">
                    <img class="post-image" src="${ image_url }" alt="Veröffentlicht am ${ timestamp }">
                </a>
                <div class="post-description">
                    ${ description }
                </div>
                <a class="post-button" href="${ url }"><i class="ri-instagram-line"></i> zum Instagram-Post</a>
            </section>
        `;
    }

    fetch("https://www.instagram.com/odermalso/?__a=1")
        .then(res => res.json())
        .then(json => {
            let posts = json["graphql"]["user"]["edge_owner_to_timeline_media"]["edges"];

            console.log(posts);

            const html = posts.map(post => getPostHTML(post)).join("");
            postContainer.innerHTML = html;
        })
</script>