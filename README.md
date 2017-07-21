# Google Calendar Events with Javascript.

This is a script to get any number of events from a public Google Calendar.

It is a modified version of Milan Kacurak's work.  I've changed various bits of logic, fixed some errors, and made some modifications to what exactly it outputs.

There are three different versions with slightly different looks to them.  Each style has 5 files that go with them.  There's the list version which is merely a text list of events.

The options for each version are the same no matter what you do.

# How To

The very first thing you need to do is ensure the calendar you want to use is set to public.  Go to Google calendar and check the settings.  This will not work if the calendar is not public.

Next you need to get an API key from Google.

[Here is a link to Google's API credentials page](https://console.developers.google.com/projectselector/apis/credentials)

Create a new project, or select an existing one.  Click on the credentials link and then click create credentials.  You want an API key.

Now, link the necessary files in your HTML document.  These should be in the `<head></head>` section of your file.

```html
<!-- js-google-calendar css file -->
<link href="google-cal-events.min.css" rel="stylesheet">
<!-- jQuery library, feel free to use any version after 1.11.3 -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
<!-- js-google-calendar js file  -->
<script src="google-cal-events.min.js"></script>
```

Now add the HTML tags wherever you want them on your page. You can change cal-past and cal-upcoming to whatever you like as long as you modify the upcomingSelector and pastSelector.  The outer div isn't necessary for these to work.

```html
<div class="cal">
      <div id="cal-past"></div>
      <div id="cal-upcoming"></div>
</div>
```

Then we just call the init function.

```javascript
<script>
      googleCalEvents.init({});
</script>
```

Inside this init function is where any customization of options will need to go.

# Options

* calendarAddress - The address of the calendar.  Typically yourname@gmail.com.  If you view the calendar's settings on the web, google lists this as the Calendar ID.
* calendarAPI - The API key you received from Google.
* past - Should past events be displayed? (boolean)
* upcoming - Should upcoming events be displayed? (boolean)
* dayNames - Should the names of days be displayed? (boolean)
* times - Should the start and end times for an event be displayed? (boolean)
* links - Should there be a link to the calendar event? (boolean)
* maxPast - Max number of past events to display. -1 is display all. (integer)
* maxUpcoming - Max number of upcoming events to display. -1 is display all. (integer)
* upcomingSelector - ID of the parent element for upcoming events. (string)
* pastSelector - ID of the parent element for past events (string)
* upcomingHeading - Markup you want placed before and outside of the parent element for upcoming events. (string)
* noUpcomingHeading - Markup that replaces upcomingHeading if there are no upcoming events. (string)
* pastHeading - Markup you want placed before and outside of the parent element for past events. (string)
* noPastHeading - Markup that replaces pastHeading if there are no past events. (string)
* format - Description of the format in which the data should be displayed. Values that will be replaced with data are listed below.  Any other value will be placed into the output as is. (array)
  * \*date\*
  * \*summary\*
  * \*description\*
  * \*location\*

# Example Initialization

```javascript
googleCalEvents.init({
      calendarAddress: 'yetaranu@gmail.com',
      calendarAPI: 'AIzaSyAPQVAhGRpl8rDGLFMdYeBAvp1mYzyLr4g',
      past: true,
      upcoming: true,
      dayNames: true,
      times: true,
      links: true,
      maxPast: 5,
      maxUpcoming: 5,
      upcomingSelector: '#cal-upcoming',
      pastSelector: '#cal-past',
      upcomingHeading: '<div class="cal-header">Upcoming Events</div>',
      noUpcomingHeading: '<div class="cal-header">There are no events coming up.</div>',
      pastHeading: '<div class="cal-header">Past Events</div>',
      noPastHeading: '<div class="cal-header">There are no past events.</div>',
      format: ['*date*', '*summary*', '*description*', '*location*']
});
```