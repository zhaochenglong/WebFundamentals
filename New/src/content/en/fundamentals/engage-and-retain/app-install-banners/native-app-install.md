project_path: /web/_project.yaml
book_path: /web/fundamentals/_book.yaml
description: Native App install banners are similar to Web app install banners, but instead of adding to the home screen will let the user install your native app without leaving your site.

{# wf_review_required #}
{# wf_updated_on: 2015-09-29 #}
{# wf_published_on: 2014-12-16 #}

# Native app Install Banners {: .page-title }

{% include "_shared/contributors/mattgaunt.html" %}
{% include "_shared/contributors/paulkinlan.html" %}

<div class="attempt-right">
  <figure>
     <img src="images/native-app-install-banner.gif" alt="Native app install banner" style="max-height: 500px">
  </figure>
</div>

Native App install banners are similar to [Web app install banners](.), but
instead of adding to the home screen, they will let the user install your
native app without leaving your site.

## Criteria to show the banner

The criteria is similar to the Web App install banner except for the need of
a service worker. Your site must:

* Have a [web app manifest](../web-app-manifest/) file with:
  - a `short_name`
  - a `name` (used in the banner prompt)
  - a 144x144 png icon, your icon declaration's should include a mime type of `image/png`
  - a `related_applications` object with information about the app
* Be served over [HTTPS](/web/fundamentals/security/encrypt-in-transit/)
* Be visited by the user twice, over two separate days during the course
  of two weeks.

## Manifest requirements

To integrate into any manifest, add a `related_applications` array with the
platforms of `play` (for Google Play) and the App Id.


    "related_applications": [
      {
      "platform": "play",
      "id": "com.google.samples.apps.iosched"
      }
    ]
    

If just want to offer the user the ability to install your Android
application, and not show the web app install banner, then add
`"prefer_related_applications": true`. For example:


    "prefer_related_applications": true,
    "related_applications": [
      {
      "platform": "play",
      "id": "com.google.samples.apps.iosched"
      }
    ]
    