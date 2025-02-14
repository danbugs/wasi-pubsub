<h1><a id="messaging"></a>World messaging</h1>
<ul>
<li>Imports:
<ul>
<li>interface <a href="#wasi_messaging_types_0_2_0_draft"><code>wasi:messaging/types@0.2.0-draft</code></a></li>
<li>interface <a href="#wasi_messaging_producer_0_2_0_draft"><code>wasi:messaging/producer@0.2.0-draft</code></a></li>
</ul>
</li>
<li>Exports:
<ul>
<li>interface <a href="#wasi_messaging_incoming_handler_0_2_0_draft"><code>wasi:messaging/incoming-handler@0.2.0-draft</code></a></li>
</ul>
</li>
</ul>
<h2><a id="wasi_messaging_types_0_2_0_draft"></a>Import interface wasi:messaging/types@0.2.0-draft</h2>
<hr />
<h3>Types</h3>
<h4><a id="client"></a><code>resource client</code></h4>
<p>A connection to a message-exchange service (e.g., buffer, broker, etc.).</p>
<h4><a id="error"></a><code>variant error</code></h4>
<p>Errors that can occur when using the messaging interface.</p>
<h5>Variant Cases</h5>
<ul>
<li>
<p><a id="error.timeout"></a><code>timeout</code></p>
<p>The request or operation timed out.
</li>
<li>
<p><a id="error.connection"></a><code>connection</code>: <code>string</code></p>
<p>An error occurred with the connection. Includes a message for additional context
</li>
<li>
<p><a id="error.other"></a><code>other</code>: <code>string</code></p>
<p>A catch all for other types of errors
</li>
</ul>
<h4><a id="message"></a><code>resource message</code></h4>
<h2>A message with a binary payload and additional information</h2>
<h3>Functions</h3>
<h4><a id="static_client_connect"></a><code>[static]client.connect: func</code></h4>
<h5>Params</h5>
<ul>
<li><a id="static_client_connect.name"></a><code>name</code>: <code>string</code></li>
</ul>
<h5>Return values</h5>
<ul>
<li><a id="static_client_connect.0"></a> result&lt;own&lt;<a href="#client"><a href="#client"><code>client</code></a></a>&gt;, <a href="#error"><a href="#error"><code>error</code></a></a>&gt;</li>
</ul>
<h4><a id="constructor_message"></a><code>[constructor]message: func</code></h4>
<h5>Params</h5>
<ul>
<li><a id="constructor_message.topic"></a><code>topic</code>: <code>string</code></li>
<li><a id="constructor_message.data"></a><code>data</code>: list&lt;<code>u8</code>&gt;</li>
</ul>
<h5>Return values</h5>
<ul>
<li><a id="constructor_message.0"></a> own&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
</ul>
<h4><a id="method_message_topic"></a><code>[method]message.topic: func</code></h4>
<p>The topic/subject/channel this message was received or should be sent on</p>
<h5>Params</h5>
<ul>
<li><a id="method_message_topic.self"></a><code>self</code>: borrow&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
</ul>
<h5>Return values</h5>
<ul>
<li><a id="method_message_topic.0"></a> <code>string</code></li>
</ul>
<h4><a id="method_message_set_topic"></a><code>[method]message.set-topic: func</code></h4>
<p>Set the topic/subject/channel this message should be sent on</p>
<h5>Params</h5>
<ul>
<li><a id="method_message_set_topic.self"></a><code>self</code>: borrow&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
<li><a id="method_message_set_topic.topic"></a><code>topic</code>: <code>string</code></li>
</ul>
<h4><a id="method_message_content_type"></a><code>[method]message.content-type: func</code></h4>
<p>An optional content-type describing the format of the data in the message. This is
sometimes described as the &quot;format&quot; type</p>
<h5>Params</h5>
<ul>
<li><a id="method_message_content_type.self"></a><code>self</code>: borrow&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
</ul>
<h5>Return values</h5>
<ul>
<li><a id="method_message_content_type.0"></a> option&lt;<code>string</code>&gt;</li>
</ul>
<h4><a id="method_message_set_content_type"></a><code>[method]message.set-content-type: func</code></h4>
<p>Set the content-type describing the format of the data in the message. This is
sometimes described as the &quot;format&quot; type</p>
<h5>Params</h5>
<ul>
<li><a id="method_message_set_content_type.self"></a><code>self</code>: borrow&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
<li><a id="method_message_set_content_type.content_type"></a><code>content-type</code>: <code>string</code></li>
</ul>
<h4><a id="method_message_data"></a><code>[method]message.data: func</code></h4>
<p>An opaque blob of data</p>
<h5>Params</h5>
<ul>
<li><a id="method_message_data.self"></a><code>self</code>: borrow&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
</ul>
<h5>Return values</h5>
<ul>
<li><a id="method_message_data.0"></a> list&lt;<code>u8</code>&gt;</li>
</ul>
<h4><a id="method_message_set_data"></a><code>[method]message.set-data: func</code></h4>
<p>Set the opaque blob of data for this message, discarding the old value</p>
<h5>Params</h5>
<ul>
<li><a id="method_message_set_data.self"></a><code>self</code>: borrow&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
<li><a id="method_message_set_data.data"></a><code>data</code>: list&lt;<code>u8</code>&gt;</li>
</ul>
<h4><a id="method_message_metadata"></a><code>[method]message.metadata: func</code></h4>
<p>Optional metadata (also called headers or attributes in some systems) attached to the
message</p>
<h5>Params</h5>
<ul>
<li><a id="method_message_metadata.self"></a><code>self</code>: borrow&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
</ul>
<h5>Return values</h5>
<ul>
<li><a id="method_message_metadata.0"></a> option&lt;list&lt;(<code>string</code>, <code>string</code>)&gt;&gt;</li>
</ul>
<h4><a id="method_message_add_metadata"></a><code>[method]message.add-metadata: func</code></h4>
<p>Add a new key-value pair to the metadata, overwriting any existing value for the same key</p>
<h5>Params</h5>
<ul>
<li><a id="method_message_add_metadata.self"></a><code>self</code>: borrow&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
<li><a id="method_message_add_metadata.key"></a><code>key</code>: <code>string</code></li>
<li><a id="method_message_add_metadata.value"></a><code>value</code>: <code>string</code></li>
</ul>
<h2><a id="wasi_messaging_producer_0_2_0_draft"></a>Import interface wasi:messaging/producer@0.2.0-draft</h2>
<p>The producer interface is used to send messages to a channel/topic.</p>
<hr />
<h3>Types</h3>
<h4><a id="client"></a><code>type client</code></h4>
<p><a href="#client"><a href="#client"><code>client</code></a></a></p>
<p>
#### <a id="message"></a>`type message`
[`message`](#message)
<p>
#### <a id="error"></a>`type error`
[`error`](#error)
<p>
----
<h3>Functions</h3>
<h4><a id="send"></a><code>send: func</code></h4>
<p>Sends the message using the given client.</p>
<h5>Params</h5>
<ul>
<li><a id="send.c"></a><code>c</code>: own&lt;<a href="#client"><a href="#client"><code>client</code></a></a>&gt;</li>
<li><a id="send.m"></a><code>m</code>: own&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
</ul>
<h5>Return values</h5>
<ul>
<li><a id="send.0"></a> result&lt;_, <a href="#error"><a href="#error"><code>error</code></a></a>&gt;</li>
</ul>
<h2><a id="wasi_messaging_incoming_handler_0_2_0_draft"></a>Export interface wasi:messaging/incoming-handler@0.2.0-draft</h2>
<hr />
<h3>Types</h3>
<h4><a id="message"></a><code>type message</code></h4>
<p><a href="#message"><a href="#message"><code>message</code></a></a></p>
<p>
#### <a id="error"></a>`type error`
[`error`](#error)
<p>
----
<h3>Functions</h3>
<h4><a id="handle"></a><code>handle: func</code></h4>
<p>Whenever this guest receives a message in one of the subscribed channels, the message is
sent to this handler. The guest is responsible for matching on the channel and handling the
message accordingly. Implementors (such as hosts) calling this interface should make their
own decisions on how to handle errors returned from this function.</p>
<h5>Params</h5>
<ul>
<li><a id="handle.ms"></a><code>ms</code>: own&lt;<a href="#message"><a href="#message"><code>message</code></a></a>&gt;</li>
</ul>
<h5>Return values</h5>
<ul>
<li><a id="handle.0"></a> result&lt;_, <a href="#error"><a href="#error"><code>error</code></a></a>&gt;</li>
</ul>
<h4><a id="subscribe"></a><code>subscribe: func</code></h4>
<p>Subscribe to a list of topics (represented as <code>string</code>s) at runtime.
Implementors should consider also allowing subscriptions to be made at compile time via
some sort of configuration file.</p>
<h5>Return values</h5>
<ul>
<li><a id="subscribe.0"></a> result&lt;list&lt;<code>string</code>&gt;, <a href="#error"><a href="#error"><code>error</code></a></a>&gt;</li>
</ul>
