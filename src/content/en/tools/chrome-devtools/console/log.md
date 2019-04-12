project_path: /web/tools/_project.yaml
book_path: /web/tools/_book.yaml
description: Learn how to log messages to the Console.

{# wf_updated_on: 2019-04-12 #}
{# wf_published_on: 2019-04-11 #}
{# wf_blink_components: Platform>DevTools #}

# Get Started With Logging Messages In The Console {: .page-title }

{% include "web/_shared/contributors/kaycebasques.html" %}

This interactive tutorial shows you how to log messages to the [Chrome DevTools](/web/tools/chrome-devtools/) Console.
You'll learn how messages get to the Console, how to log messages from your JavaScript, and how to filter messages.

<figure>
  <img src="/web/tools/chrome-devtools/console/images/logexample.png"
       alt="Messages in the Console.">
  <figcaption>
    <b>Figure X</b>. Messages in the Console.
  </figcaption>
</figure>

TODO prerequisites

## A note on quizzes {: #quiz }

This tutorial contains quizzes.

## Set up the demo and DevTools {: #setup }

This is an interactive tutorial. TODO learning

1. Open the demo.
1. (Optional) Move the demo to a separate window.
1. Focus the demo and then press <kbd>Control</kbd>+<kbd>Shift</kbd>+<kdb>J</kbd> or
   <kbd>Control</kbd>+<kbd>Shift</kbd>+<kdb>J</kbd> (Mac) to open DevTools. By default DevTools opens to the
   right of the demo.
1. (Optional) Dock DevTools to the bottom of the window or undock it into a separate window.

## Log messages from JavaScript {: #javascript }

Most messages that you see in the Console come from the web developers who wrote the page's JavaScript.
The goal of this section is to introduce you to the different message types that you're likely to see in the Console, and
explain how you can log each message type yourself from your own JavaScript.

1. Click the **Log Greeting** button in the demo. `Hello, Console!` gets logged to the Console.

1. Next to the `Hello, Console!` message in the Console click **log.js:X**. The Sources panel opens and highlights the
   line of code that caused the message to get logged to the Console. The message was logged when the page's JavaScript
   called `console.log('Hello, Console!')`.

1. Navigate back to the Console using any of the following workflows:

     * Click the **Console** tab.
     * Press <kbd>Control</kbd>+<kbd>[</kbd> or <kbd>Command</kbd>+<kbd>[</kbd> (Mac) until the Console panel is in focus.
     * [Open the Command Menu](/web/tools/chrome-devtools/command-menu), start typing `Console`, select the
       **Show Console Panel** command, and then press <kbd>Enter</kbd>.

1. Click the **Log Warning** button in the demo. `Abandon Hope All Ye Who Enter` gets logged to the Console.
   Messages formatted like this are warnings.

1. (Optional) Click **log.js:X** to view the code that caused the message to get formatted like this, and then navigate
   back to Console when you're finished. Do this whenever you want to figure out why a message was logged in a certain way.

[trace]: https://en.wikipedia.org/wiki/Stack_trace

1. Click the **Expand** icon in front of the `Log Warning` message in the Console. DevTools
   shows the [stack trace][trace]{: .external } leading up to the call. When the button's `click` event listener
   fired, it called `logWarning`, which in turn called `quoteDante`, which in turn called
   `console.warn('Abandon Hope All Ye Who Enter')`. In other words, the call that happened first is at the
   bottom of the trace. You can manually log stack traces at any time by calling `console.trace()`.

1. Click **Log Error**. `I'm sorry, Dave. I'm afraid I can't do that.` gets logged to the Console.
   Messages formatted like this are errors.

1. Click **Log Table**. Log tables by calling `console.table(arrayOfObjects)`, where
   `arrayOfObjects` is an array of objects with similar properties. For example, in **Figure X** each
   object has a `first` and `last` property, so those columns are populated in each row. Only one of the objects
   has a `birthday` property, so that column isn't populated in some of the rows.

1. Click **Log Group**. Log groups by calling `console.group(label)`,
   where `label` is the name of the group. Any subsequent `console` call, such as `console.log('Leo')`, is
   grouped together until `console.groupEnd(label)` is called. The `label` must be the same as before in order
   to end the group.

1. Click **Log Custom**. A message with custom formatting gets logged to the Console. 

### View messages logged by the browser {: #browser }

The browser logs messages to the Console, too. This usually happens when there's a problem with the page.

1. Click **Cause 404**. The browser logs a `404` network error because the page's JavaScript tried to
   fetch a file that doesn't exist, `https://devtools.glitch.me/coffee`.

1. Click **Cause Error**. The browser logs an uncaught `TypeError` because the JavaScript is trying to update
   a DOM node that doesn't exist.

1. Click **Throw Error**. The browser logs a `TypeError`. 

       {% framebox width="auto" height="auto" enable_widgets="true" %}
         <button class="gc-analytics-event" data-category="DevTools"
                 data-label="Console / Get Started / 1.B.1 (TypeError)">Throw Error</button>
         <script>
           const button = document.querySelector('button');
           button.addEventListener('click', function () {
             boosh.howard = "I don't buffet about in the winds of fashion.";
           });
         </script>
       {% endframebox %}

     The browser throws this error because the button's click listener is trying to access an object
     property that doesn't exist.

1. Click **Throw 404**. The browser logs a `404 (Not Found)` error, as well as others.

       {% framebox width="auto" height="auto" enable_widgets="true" %}
         <button class="gc-analytics-event" data-category="DevTools"
                 data-label="Console / Get Started / 1.B.2 (404)">Throw 404</button>
         <script>
           const button = document.querySelector('button');
           button.addEventListener('click', function () {
             const url = "not/a/real/file.png";
             fetch(url);
           });
         </script>
       {% endframebox %}

     The browser throws these errors when a page tries to request a file that doesn't exist.

### Part C: Filter messages {: #filter }

On big sites, you'll sometimes see the **Console** get flooded with messages. You can
filter the **Console** to only show messages that you care about.

1. Click **Log Numbers**. The **Console** prints out whether each number from 1 to 1000 is prime.
   Every third message is printed with `console.warn()`. In real life you should only use
   `console.warn()` for warning scenarios, but this is just a contrived example to demonstrate
   filtering.

     {% framebox width="auto" height="auto" enable_widgets="true" %}
       {% includecode content_path="web/tools/chrome-devtools/console/_code/primes.html" %}
     {% endframebox %}

1. Type `123` in the **Filter** text box. The **Console** only shows messages that contain
   `123` in either the content of the message, or the filename that caused the message.
1. Replace `123` with `-not`. The **Console** hides any message that contains `not`.
   Using the pattern `-<text>` hides any message that includes `<text>`.
1. Replace `-not` with `/1[0-9]1/`, which is a [regular expression][regex]{:.external}.
   The **Console** only shows messages that include a 3-digit number that starts with `1` and
   ends with `1`. Keep the filter enabled and continue to the next step.

[sidebar]: /web/tools/chrome-devtools/images/shared/show-console-sidebar.png

1. Click **Show Console Sidebar** ![Show Console Sidebar][sidebar]{: .inline-icon }.
   The **Sidebar** lets you further filter messages by type.
1. Click **333 Warnings**. DevTools now only shows messages that were logged with
   `console.warn()`. Remember that the `/1[0-9]1/` filter is still active, so you actually
   are filtering along 2 dimensions right now.

     <figure>
       <img src="images/sidebar-regex.png"
            alt="Filtering with the Sidebar and a regular expression, simultaneously.">
       <figcaption>
         <b>Figure 5</b>. Filtering with the <b>Sidebar</b> and a regular expression,
         simultaneously
       </figcaption>
     </figure>

1. Close the **Sidebar** and delete `/1[0-9]1/` from the **Filter** text box.

[regex]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions



## Next steps {: #next-steps }



## Feedback {: #feedback }

{% include "web/_shared/helpful.html" %}

{# Runs on page load. #}

{% framebox width="0px" height="0px" enable_widgets="true" %}
  <script>
    console.log('%cWelcome to the Console!', 'font-weight:bold;color:#317efb;font-style:italic',
        'Read on to learn how messages like this get here.');
  </script>
{% endframebox %}

