# Introduction #

CSipSimple is still under heavy development. If you notice a force close or an error while running the app.
The first good reflex is to search on the Issue section if you are alone with the problem.
Then if you found nothing corresponding to your issue, you can open a new one. One thing that can do the fix of your issue quicker is to provides logs to allow developers to understand what has happened.

# How to turn on logging on CSipSimple #

  1. Press the menu button on the main CSipSimple view (the dialer),
  1. Choose Help and press "Record logs to send it to dev team and report a bug".
  1. Go back using the back button.

![http://www2.r3gis.fr/CSSPublic/tuto/collect_logs/step_1.png](http://www2.r3gis.fr/CSSPublic/tuto/collect_logs/step_1.png)
![http://www2.r3gis.fr/CSSPublic/tuto/collect_logs/step_2.png](http://www2.r3gis.fr/CSSPublic/tuto/collect_logs/step_2.png)

# Reproduce your bug now #

You can now reproduce your bug (if possible) logs are recorded.

# How to get back the logs and what to do with the logs #

  1. Press the menu button on the main CSipSimple view
  1. Choose Help and press "Stop recording logs (OPTIONALY send it)".
  1. After a little while it asks for an app to use to send the logs (usually gmail or email). If there is no app to send email this method will not work.
  1. In the body describe your problem or the issue of the issue list associated if you opened one.

![http://www2.r3gis.fr/CSSPublic/tuto/collect_logs/step_3.png](http://www2.r3gis.fr/CSSPublic/tuto/collect_logs/step_3.png)

# Alternate solution 1 #
If it doesn't work for any reason you can :
  1. Follow the turn on logging step in first paragraph above.
  1. Install log-collector : http://code.google.com/p/android-log-collector/ (available both on the market and on their website).
  1. Reproduce the problem
  1. Launch log-collector
  1. Log-collector will ask you how you want to send logs, choose mail and send it to developers [at ](.md) csipsimple [dot](dot.md) com.

# Alternate solution 2 #
  1. Activate ExpertSettingMode (see wiki page)
  1. Go in _User Interface_ section
  1. Change log level to 4
  1. Activate log to file.
  1. Go back twice to go in dialer.
  1. Reproduce the problem
  1. Go in settings and press back once (this will flush the file)
  1. Get the log files from the sdcard in CSipSimple/logs folder.
  1. Send it by any mean you want to developers [at ](.md) csipsimple [dot](dot.md) com.