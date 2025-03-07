
Context is extra information you can record about any call to our API. It can be anything you want, like `ip` address, `userAgent`, `location`, etc. For example, our iOS SDK will automatically send `os.version` as context with each request.

You can record context by sending an extra `context` dictionary to any of the method calls in any of our [libraries](/docs/connections/sources/). You aren't required to send context, but it can be useful if you want to access any extra information in your raw logs that isn't specific to a user, group or event.


## Special Context

Some context key names have semantic meaning, and we handle them in special ways. For example, we always expect `ip` to be the current IP address of the user, and we'll use that to determine their location in certain cases.

You should **only use** special context keys for their intended meaning. Many of them are automatically collected from our [libraries](/docs/connections/sources/), like `app.version` is from our iOS SDK.

Here's a list of the special context keys we recognize, case insensitive:

<table>
  <tr>
    <td markdown="span">`app`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of information about the current application, containing `name`, `version` and `build`. This is collected automatically from our mobile libraries when possible.</td>
  </tr>
  <tr>
    <td markdown="span">`campaign`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of information about the campaign that resulted in the API call, containing `name`, `source`, `medium`, `term` and `content`. This maps directly to the common UTM campaign parameters.</td>
  </tr>
  <tr>
    <td markdown="span">`device`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of information about the device, containing `id`, `manufacturer`, `model`, `name`, `type` and `version`.</td>
  </tr>
  <tr>
    <td markdown="span">`ip`</td>
    <td markdown="span">String</td>
    <td markdown="span">The current user's IP address.</td>
  </tr>
  <tr>
    <td markdown="span">`library`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of information about the library making the requests to the API, containing `name` and `version`.</td>
  </tr>
  <tr>
    <td markdown="span">`locale`</td>
    <td markdown="span">String</td>
    <td markdown="span">The locale string for the current user, for example `en-US`.</td>
  </tr>
  <tr>
    <td markdown="span">`location`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of information about the user's current location, containing `city`, `country`, `latitude`, `longitude`, `region` and `speed`.</td>
  </tr>
  <tr>
    <td markdown="span">`network`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of information about the current network connection, containing `bluetooth`, `carrier`, `cellular` and `wifi`.</td>
  </tr>
  <tr>
    <td markdown="span">`os`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of information about the operating system, containing `name` and `version`.</td>
  </tr>
  <tr>
    <td markdown="span">`referrer`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of information about the way the user was referred to the website or app, containing `type`, `name`, `url` and `link`.</td>
  </tr>
  <tr>
    <td markdown="span">`screen`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of information about the device's screen, containing `density`, `height` and `width`.</td>
  </tr>
  <tr>
    <td markdown="span">`timezone`</td>
    <td markdown="span">String</td>
    <td markdown="span">Timezones are sent as tzdata strings to add user timezone information which might be stripped from the timestamp, for e.g. `America/New_York`</td>
  </tr>
  <tr>
    <td markdown="span">`traits`</td>
    <td markdown="span">Object</td>
    <td markdown="span">A dictionary of `traits` of the current user. This is useful in cases where you need to `track` an event, but also associate information from a previous `identify` call.</td>
  </tr>
  <tr>
    <td markdown="span">`userAgent`</td>
    <td markdown="span">String</td>
    <td markdown="span">The user agent of the device making the request.</td>
  </tr>
</table>

If you wanted to record extra information about the device, for example its `color`, you could stick that information inside the same `device` dictionary, and that will be merged with the automatically collected device information by any of our [libraries](/docs/connections/sources/).
