project_path: /web/tools/_project.yaml
book_path: /web/tools/_book.yaml
description: The main uses of the Chrome DevTools Console are logging messages and running JavaScript.

{# wf_updated_on: 2019-04-09 #}
{# wf_published_on: 2019-04-09 #}
{# wf_blink_components: Platform>DevTools #}

[GS]: /web/tools/chrome-devtools/console/get-started

# Console Overview {: .page-title }

{% include "web/_shared/contributors/kaycebasques.html" %}

This page explains how the Chrome DevTools Console makes it easier to develop web pages.
The Console has 2 main uses: [viewing logged messages](#view) and [running JavaScript](#javascript).

## Viewing logged messages {: #view }

Web developers often log message to the Console to make sure that their JavaScript is working as expected. For example,
suppose that you're in the process of writing the HTML and JavaScript for a page. Here's your code:

    <!doctype html>
    <html>
      <head>
        <title>Console Demo</title>
      </head>
      <body>
        <h1>Hello, World!</h1>
        <script>
          console.log('Loading!');
          const h1 = document.querySelector('h1');
          console.log(h1.textContent);
          console.assert(document.querySelector('h2'), 'h2 not found!');
          const artists = [
            {
              first: 'René',
              last: 'Magritte',
            },
            {
              first: 'Chaim',
              last: 'Soutine',
            },
            {
              first: 'Henri',
              last: 'Matisse',
            },
          ];
          console.table(artists);
          setTimeout(() => {
            h1.textContent = 'Hello, Console!';
            console.log(h1.textContent);
          }, 3000);
        </script>
      </body>
    </html>

Figure X shows what the Console looks like after loading the page and waiting 3 seconds.

Web developers log messages like this for 2 general reasons:

* Making sure that the code is executing in the right order.
* Inspecting the values of variables at a certain moment in time.

To log messages to the Console, all you need to do is insert expressions like `console.log('Loading!')` into
your code. See [Get Started With Logging Messages](/web/tools/chrome-devtools/console/log) to learn more
about logging. See the [Console API Reference](/web/tools/chrome-devtools/console/api) to browse the full list
of `console` methods. The main difference between the methods is how they display the data
that you're logging.

## Running JavaScript {: #javascript }

## Next steps {: #CTA }

See [Get Started][GS] to get hands-on practice with the Console.

## Feedback {: #feedback }

{% include "web/_shared/helpful.html" %}
