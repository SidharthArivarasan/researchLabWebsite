---
# Leave the homepage title empty to use the site title
title:
date: 2022-10-24
type: landing

sections:
  - block: hero
    content:
      title: |
        Wowchemy
        Research Group
      image:
        filename: welcome.jpg
      text: |
        <br>
        
        The **Wowchemy Research Group** has been a center of excellence for Artificial Intelligence research, teaching, and practice since its founding in 2016.
  
  - block: collection
    content:
      title: Latest News
      subtitle:
      text:
      count: 5
      filters:
        author: ''
        category: ''
        exclude_featured: false
        publication_type: ''
        tag: ''
      offset: 0
      order: desc
      page_type: post
    design:
      view: card
      columns: '1'
  
  - block: markdown
    content:
      title: "Live News Feed from Strapi"
      subtitle: ""
      text: |
        <div id="strapi-news-feed" class="news-grid"></div>

        <script>
          fetch("https://rlw-strapi.onrender.com/api/newss")
            .then(res => res.json())
            .then(json => {
              const data = json.data || [];
              const container = document.getElementById("strapi-news-feed");

              if (!container) return;

              if (data.length === 0) {
                container.innerHTML = "<p>No news available.</p>";
                return;
              }

              data.forEach((item) => {
                container.innerHTML += `
                  <div class='news-item'>
                    <h3>${item.title}</h3>
                    <p>${item.summary}</p>
                    <a href="#">Read more</a>
                    <hr />
                  </div>
                `;
              });
            })
            .catch(err => {
              document.getElementById("strapi-news-feed").innerHTML = "<p>Failed to load news.</p>";
              console.error("Strapi fetch error:", err);
            });
        </script>
    design:
      columns: '1'

  - block: markdown
    content:
      title:
      subtitle: ''
      text:
    design:
      columns: '1'
      background:
        image: 
          filename: coders.jpg
          filters:
            brightness: 1
          parallax: false
          position: center
          size: cover
          text_color_light: true
      spacing:
        padding: ['20px', '0', '20px', '0']
      css_class: fullscreen

  - block: collection
    content:
      title: Latest Preprints
      text: ""
      count: 5
      filters:
        folders:
          - publication
        publication_type: 'article'
    design:
      view: citation
      columns: '1'

  - block: markdown
    content:
      title:
      subtitle:
      text: |
        {{% cta cta_link="./people/" cta_text="Meet the team →" %}}
    design:
      columns: '1'
---
