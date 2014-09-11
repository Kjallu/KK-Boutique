KK-Boutique
===========

All you need...
 fashion

<!DOCTYPE html>
<link rel="stylesheet" href="/adorn/adorn.css"/>
<script src="/adorn/adorn.js"></script>

<title>Hello.js Modules</title>

<h1>HelloJS Modules</h1>

<p>HelloJS is extensible, i.e. you can add new services to it as long as you can get your head around the important parts.

<blockquote>
	<p>Modules are just small javascript scripts that define the URL's for things like the login page and the REST'ful webserver. They're also a place which standardise a naming convention e.g. path locations, scopes, data response and delivery mechanisms.
</blockquote>

<h2>HelloJS already has you connected</h2>
<p>The table shows the services which are already documented on HelloJS. Simply include these scripts in your page after your HelloJS script tag</p>
<table>
	<thead>
		<tr>
			<th>extension</th>
			<th>demo</th>
			<th>credits</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><a href="./src/modules/dropbox.js">dropbox.js</a></td>
			<td><a href="demos/dropbox.html">dropbox demo</a></td>
			<td></td>
		</tr>
		<tr>
			<td><a href="./src/modules/facebook.js">facebook.js</a></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td><a href="./src/modules/foursquare.js">foursquare.js</a></td>
			<td><a href="demos/foursquare.html">foursquare demo</a></td>
			<td></td>
		</tr>
		<tr>
			<td><a href="./src/modules/github.js">github.js</a></td>
			<td><a href="demos/github.html">github demo</a></td>
			<td></td>
		</tr>
		<tr>
			<td><a href="./src/modules/google.js">google.js</a></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td><a href="./src/modules/linkedin.js">linkedin.js</a></td>
			<td><a href="demos/linkedin.html">linkedin demo</a></td>
			<td></td>
		</tr>
		<tr>
			<td><a href="./src/modules/soundcloud.js">soundcloud.js</a></td>
			<td><a href="demos/soundcloud.html">soundcloud demo</a></td>
			<td></td>
		</tr>
		<tr>
			<td><a href="./src/modules/twitter.js">twitter.js</a></td>
			<td><a href="demos/twitter.html">twitter demo</a></td>
			<td></td>
		</tr>
		<tr>
			<td><a href="./src/modules/windows.js">windows.js</a></td>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td><a href="./src/modules/yahoo.js">yahoo.js</a></td>
			<td><a href="demos/yahoo.html">yahoo demo</a></td>
			<td></td>
		</tr>
	</tbody>
</table>

<h2>Writing your own module</h2>
<p>Modules are loaded into helloJS using the hello.init() method, with a JSON object that has the name of the service as the only key and then whose value consists of an object with the following parameters.</p>
<table>

	<thead>
		<tr>
			<th>name</th>
			<th>type</th>
			<th>example</th>
			<th>description</th>
			<th>argument</th>
			<th>default</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>url</td>
			<td><i>Object<i></td>
			<td></td>
			<td>An array=&gt;key map of the paths to translate. The keys "auth" and "base" are required</td>
			<td>required</td>
			<td></td>
		</tr>
		<tr>
			<td>oauth</td>
			<td colspan="3">
				<i>Object</i>
				<table>
					<thead><tr><th>name</th><th>type</th><th>description</th></tr></thead>
					<tbody>
						<tr>
							<td>version</td>
							<td>string</td>
							<td>Version of OAuth, "1.0", "1.0a", "2"</td>
						</tr>
						<tr>
							<td>request</td>
							<td>url</td>
							<td>Path of the first leg of OAuth 1</td>
						</tr>
						<tr>
							<td>auth</td>
							<td>url</td>
							<td>Path of the authorization URL, second leg of OAuth 1</td>
						</tr>
						<tr>
							<td>token</td>
							<td>url</td>
							<td>Path to get the Access token, the third leg of OAuth 1</td>
						</tr>
					</tbody>
				</table>
			</td>
			<td>optional*</td>
			<td></td>
		</tr>
		<tr>
			<td>refresh</td>
			<td><i>Boolean<i></td>
			<td></td>
			<td>Indicate that the providers supports silent signin, aka display=none, however if a refresh_token was proffered at signin, then an attempt will be made with that.</td>
			<td>optional</td>
			<td>false</td>
		</tr>
		<tr>
			<td>scope</td>
			<td><i>Object<i></td>
			<td></td>
			<td>An array=&gt;key map of the scopes to translate</td>
			<td>optional</td>
			<td></td>
		</tr>
		<tr>
			<td>scope_delim</td>
			<td><q>string</q></td>
			<td><q>,</q>, <q> </q></td>
			<td>Overrides the default delmiter between multiple scopes</td>
			<td>optional</td>
			<td><q>,</q></td>
		</tr>
		<tr>
			<td>wrap</td>
			<td><i>Object<i></td>
			<td></td>
			<td>An array=&gt;key map of pathnames, used to pre-process the response objects returned</td>
			<td>optional</td>
			<td></td>
		</tr>
		<tr>
			<td>querystring</td>
			<td><i>function<i></td>
			<td></td>
			<td>A function to preprocess the querystring</td>
			<td>optional</td>
			<td>true</td>
		</tr>
		<tr>
			<td>xhr</td>
			<td><i>function<i></td>
			<td></td>
			<td>A function which if the browser supports XHR2 can be used to augment the request further, the function can return a boolean false to cancel this delivery mechanism and fallback to another</td>
			<td>optional</td>
			<td>true</td>
		</tr>
		<tr>
			<td>jsonp</td>
			<td><i>function<i></td>
			<td></td>
			<td>A function which if the data lends itself to transport over JSONP can be used to augment the request further, the function can return a boolean false to cancel this delivery mechanism and fallback to another</td>
			<td>optional</td>
			<td></td>
		</tr>
		<tr>
			<td>post</td>
			<td><i>function<i></td>
			<td></td>
			<td>A function which if the browser supports the Form+Iframe+Hash hack, can be used to augment the request further, the function can return a boolean false to cancel this delivery mechanism and fallback to another</td>
			<td>optional</td>
			<td></td>
		</tr>
	</tbody>
</table>
<p>*optional: If the service is an OAuth 1.0/1.0a version then 'oauth' object is required.</p>
<h2>Contributing modules</h2>
<p>That would be fantastic if you could. Please make the following updates so its easiy for people to discover and test.</p>
<ul>
	<li>Fork the code from GitHub
	<li>Name your script with the label you want it to be identified with and use this as the key name of module settings above
	<li>Add your module to tests/hello.all.js
	<li>Check your script passes the test in as many browsers as you can.
	<li>Update the list of services above with a name and link, also get credit for your hard work by including your name
</ul> 
