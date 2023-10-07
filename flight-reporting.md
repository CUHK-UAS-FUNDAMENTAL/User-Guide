# Flight Reporting

PX4 logs detailed aircraft state and sensor data, which can be used to analyze performance issues. This topic explains how you can download and analyse logs, and share them with the development team for review.

TIP

Keeping flight logs is a legal requirement in some jurisdictions.

### [#](broken-reference) Downloading Logs from the Flight Controller <a href="#downloading-logs-from-the-flight-controller" id="downloading-logs-from-the-flight-controller"></a>

Logs can be downloaded using [QGroundControl (opens new window)](http://qgroundcontrol.com/): [**Analyze View > Log Download (opens new window)**](https://docs.qgroundcontrol.com/master/en/analyze\_view/log\_download.html).

### [#](broken-reference) Analyzing the Logs <a href="#analyzing-the-logs" id="analyzing-the-logs"></a>

Upload the log file to the online [Flight Review (opens new window)](http://logs.px4.io/) tool. After upload you'll be emailed a link to the analysis page for the log.

Log Analysis using Flight Review explains how to interpret the plots, and can help you to verify/reject the causes of common problems: excessive vibration, poor PID tuning, saturated controllers, imbalanced vehicles, GPS noise, etc.

Note

There are many other great tools for visualising and analysing PX4 Logs. For more information see: Flight Analysis.

### [#](broken-reference) Sharing the Log Files for Review by PX4 Developers <a href="#sharing-the-log-files-for-review-by-px4-developers" id="sharing-the-log-files-for-review-by-px4-developers"></a>

The [Flight Review (opens new window)](http://logs.px4.io/) log file link can be shared for discussion in the [support forums](https://about/main/en/contribute/support.html#forums-and-chat) or a [Github issue](https://about/main/en/#reporting-bugs-issues).

### [#](broken-reference) Log Configuration <a href="#log-configuration" id="log-configuration"></a>

The logging system is configured by default to collect sensible logs for use with [Flight Review (opens new window)](http://logs.px4.io/).

Logging may further be configured using the [SD Logging](https://about/main/en/advanced\_config/parameter\_reference.html#sd-logging) parameters or with a file on the SD card. Details on configuration can be found in the [logging configuration documentation](https://about/main/en/dev\_log/logging.html#configuration).

### [#](broken-reference) Key Links <a href="#key-links" id="key-links"></a>

* [Flight Review (opens new window)](http://logs.px4.io/)
* Log Analysis using Flight Review
* Flight Log Analysis

Last Updated: 7/10/2023, 10:18:26 PM
