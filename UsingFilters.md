# Introduction #
<img src='http://solo.dc3.com/extimage/csfilt1-sm.png' align='right' />

It is often useful to be able to alter certain actions based on the phone number to be dialed. Also, sometimes the contact phone numbers are in a form that cannot be used for SIP calls, and thus need to be rewritten for the needs of the SIP switch/account. These things are handled by **filters** in the application. Important points:

  * Filters are applied when the application's "outgoing call chooser" appears:<br> <img src='http://solo.dc3.com/extimage/csfilt5-sm.png' />
<ul><li>Filters are specific to each account.<br>
</li><li>Filters may also be set for the native phone dialer.<br>
</li><li>A filter has a match type and pattern (a <i>rule</i>), plus an action to perform if the phone number matches the rule.<br>
</li><li>A filter operates based on the rule, and if the phone number matches the rule, the selected action occurs.<br>
</li><li>There are several types of matching such as <i>starts-with</i> and <i>ends-with</i>.<br>
</li><li>Multiple filters may be set up for an account or the dialer.<br>
</li><li>If multiple filters are set, they are run in the order listed<br>
</li><li>Mutiple rewriting filters may be set up, and the input to each is the output of the previous rewrite filter, or the original number for the first rewrite filter in the list.<br>
</li><li>The application will automatically remove separators (e.g., spaces, parentheses, and '-') from phone numbers before sending them through the filters.</li></ul>

Filters are a very powerful feature of the application, so use your imagination and creativity and you can probably solve the problem you have. Filters are much more powerful and flexible than the more common "dial plan" features found on other SIP phones.<br>
<br>
<h1>Creating and Editing Filters</h1>

The filters editor is one of the settings categories. We won't give touch-by-touch directions here, it's assumed you'll be able figure the user interface out. It is intuitive and simple. Once you're in the filters main screen, you'll see a list of SIP accounts and, at the bottom, a Dialer entry (which acts like an account but for the native dialer). Touching an account starts the filter editor for that account. Now you can add a new filter or edit an existing one (by touching it in the list). Delete a filter with a long-touch and then touching <i>Delete filter</i>.<br>
<br>
<h2>Some Common Examples of Filter Use</h2>

Most commonly, filters are used for implementing "dial plans" as used on other SIP phones. Let's say you have contacts in your phone which have full international/<a href='http://en.wikipedia.org/wiki/E.123'>E.123</a> format phone numbers, an internal extension number, and a <a href='#SIP_Addresses.md'>full SIP address</a>:<br>
<img src='http://solo.dc3.com/extimage/csfilt4-sm.png' />

Let's also say your country code is 1 and you have a SIP account for a provider or company switch and it requires the following number formats for successful (outside) dialing:<br>
<br>
<ul><li><b>National calling:</b> 1 followed by the area code and number (14513297452)<br>
</li><li><b>International calling:</b> 011 followed by the country code, area code, and number (01144632548721)<br>
</li><li><b>Emergency:</b> 911</li></ul>

See <a href='#Multiple_Filters.md'>Multiple Filters</a>

<h3>International Format Numbers</h3>

Your full phone numbers are in E.123 format, so some rewriting will be needed on the account for your provider or company switch:<br>
<br>
<ul><li>If the number starts with +1 just remove the +<br>
</li><li>Otherwise, remove the + and prepend 011</li></ul>

In the US, mobile phone companies use these same formats, so you will need the same filters applied to the Dialer. By the way, there is a very useful Android application <a href='http://code.google.com/p/android-contacts-cleanup/'>Contacts Cleanup</a> which will format all of your contact phone numbers into the international/E.123 format.<br>
<br>
<h3>Internal Extensions</h3>

For a company SIP switch, internal extensions (usually just three digits) cannot be dialed with the mobile Dialer and must always be dialed via your company SIP switch account. For this, you would use a filter on your company switch account which looks for exactly 3 digits and has an action of <i>direct call</i>. This forces the application to immediately use the company switch account for internal extensions. The outgoing call chooser never appears.<br>
<br>
In the US, emergency dialing is also three digits, 911. Let's say you want 911 to always be dialed with your mobile phone and not any SIP account (so the E911 service gets your GPS coordinates). For this, you would use a filter on the mobile dialer that looks for exactly 911 and has an action of <i>direct call</i>. This forces the application to immediately use the mobile dialer for emergency calls. The outgoing call chooser never appears.<br>
<br>
<h3>SIP Addresses</h3>

The application will treat a custom IM address with the label <b>SIP</b> as a phone number. It should be a full SIP URI such as george-mobile@sip.acme.com, so it will contain an '@'. Clearly this cannot be dialed via the mobile dialer, and you probably want to use a specific account to make these direct SIP calls. On that account, use a filter on the account that looks for @ in the "number" and has an action of <i>direct call</i>. This forces the application to immediately use that account for direct SIP calls. The outgoing call chooser never appears.<br>
<br>
<h2>Multiple Filters</h2>

You can create multiple filters on an account. They will be run in the order listed. <u>You can reorder the filters by dragging and dropping</u>. Touch and drag by the gray icon on the left edge of the filter entry in the list. Note that the <i>Can't call</i> and <i>Directly call</i> filter actions happen immediately; any filters listed afterward will not run if these actions occur.<br>
<br>
<h1>Reference</h1>
<img src='http://solo.dc3.com/extimage/csfilt3-sm.png' align='right' />
This section describes the filter rules and the actions that can occur if the phone number matches the rule. A <i>rule</i> consists of a match type and some value you supply such as a match pattern or a numeric value. An <i>action</i> is what happens if the rule is matched. In the filter editor, the action is selected at the top and the rule is specified in the box below that. If the action is <i>Rewrite</i> a third area appears in which you specify some prefix, suffix, or replacement text.<br>
<br>
<h2>Actions</h2>

<h3>Can't Call</h3>

A matching number will prevent this account from showing in the outgoing call chooser.<br>
<br>
<h3>Directly Call</h3>

A matching number will force this account to be immediately used for calling. The outgoing call chooser will not be shown.<br>
<br>
<h3>Rewrite</h3>

A matching number will be rewritten according to the <a href='UsingFilters#Replacements.md'>replacement action</a>. The rewritten number will be passed along to the next filter (if any) as input.<br>
<br>
<h3>Stop Processing</h3>

A matching number will not be passed along to the next filter (if any). Instead, it will be used as-is.<br>
<br>
<h3>Auto Answer</h3>

<i>to be written</i>

<h2>Match Types</h2>

Numbers can consist of digits, letters, and/or punctuation.<br>
<br>
<h3>Starts with</h3>

The number is matched if it starts with the given text.<br>
<br>
<h3>Ends with</h3>

The number is matched if it ends with the given text.<br>
<br>
<h3>Contains</h3>

The number is matched if it contains the given text anywhere within it.<br>
<br>
<h3>All</h3>

The number is always matched.<br>
<br>
<h3>Has exactly N digit</h3>

The number is matched if it is exactly the given length.<br>
<br>
<h3>Has more than N digit</h3>

The number is matched if it is the given length or longer.<br>
<br>
<h3>Is exactly</h3>

The number is matched if it is exactly the same as the given text.<br>
<br>
<h3>Custom RegExp</h3>

Matching is specified by the given <a href='http://developer.android.com/reference/java/util/regex/Pattern.html'>Java regular expression</a>. The regular expression pattern can contain one or more <i>capturing groups</i>, useful for Rewrite filters with the Custom RegExp replacement type.<br>
<br>
<h2>Replacement Types</h2>

This applies only to the <a href='UsingFilters#Rewrite.md'>Rewrite action</a>.<br>
<br>
<h3>Prefix by</h3>

The given text is put before the beginning of the matched text in the number.<br>
<br>
<h3>Suffix with</h3>

The given text is put at the end of the matched text in the number.<br>
<br>
<h3>Replace match by</h3>

The given text replaces the matched text in the number. The unmatched text in the number remains. Examples:<br>
<br>
<ul><li>3451209 starts with 345 replace match with 987 results in 9871209.<br>
</li><li>joe@foo.com contains foo replace match with bar results in joe@bar.com</li></ul>

<h3>Replace all by</h3>

The given text replaces the entire number.<br>
<br>
<h3>Custom RegExp</h3>

Useful only if the match type is also Custom RegExp, and if the match regular expression pattern contains one or more <i>capturing groups</i>. In this case, the captured text for each group (left to right) can be specified with $1, $2, etc,. and the entire matched string can be specified with $0. For more information see the documentation of <a href='http://developer.android.com/reference/java/util/regex/Pattern.html'>java.util.regex.Pattern</a>.<br>
<br>
<h1>Tips and Tricks</h1>

<i>to be written</i>