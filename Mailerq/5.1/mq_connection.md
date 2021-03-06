# Structure MQ_Connection

The [MQ_Connection](mq_connection) structure is passed to all callbacks 
dealing with SMTP connections. It allows your plugin to find out information 
about the connection, and to send data over the connection.

## Functions that your plugin can export

There is a whole list of functions that your plugin can export that deal with 
connections.

<table>
    <tr>
        <td><a href="mq_smtp_in_connect">mq_smtp_in_connect()</a></td>
        <td>Called after an incoming TCP connection is established. This is the first time that the <a href="mq_connection">MQ_Connection</a> is passed to the plugin, and a good place for per-connection initialization code.</td>
    </tr>
    <tr>
        <td><a href="mq_smtp_in_secure">mq_smtp_in_secure()</a></td>
        <td>Called when the STARTTLS instruction is received and the connection is turned into a secure connection</td>
    </tr>
    <tr>
        <td><a href="mq_smtp_in_authenticate">mq_smtp_in_authenticate()</a></td>
        <td>Called when the SMTP client sends the login+password credentials. Allows you to run your own authentication checks.</td>
    </tr>
    <tr>
        <td><a href="mq_smtp_in_mailfrom">mq_smtp_in_mailfrom()</a></td>
        <td>Called when the "MAIL FROM" command is received</td>
    </tr>
    <tr>
        <td><a href="mq_smtp_in_rcptto">mq_smtp_in_rcptto()</a></td>
        <td>Called when the "RCPT TO" command is received</td>
    </tr>
    <tr>
        <td><a href="mq_smtp_in_data">mq_smtp_in_data()</a></td>
        <td>Called when the "DATA" command is received</td>
    </tr>
    <tr>
        <td><a href="mq_smtp_in_message">mq_smtp_in_message()</a></td>
        <td>Called when a message is received. When multiple "RCPT TO" addresses were given, this function is called once for each address.</td>
    </tr>
    <tr>
        <td><a href="mq_smtp_in_close">mq_smtp_in_close()</a></td>
        <td>Called after an incoming SMTP connection is closed. This is the last time that the <a href="mq_connection">MQ_Connection</a> is passed to the plugin. You can use this function for cleanup code.</td>
    </tr>
</table>

The above functions are only called for [MQ_Connection](mq_connection) pointers 
that represent _incoming_ connections.

## Access to connection properties

All members in the [MQ_Connection](mq_connection) structure are private. To interact 
with the structure the following accessor functions have been created.

| Callable function                                                   | Description                                                   |
|---------------------------------------------------------------------|---------------------------------------------------------------|
| [MQ_fileDescriptor()](mq_filedescriptor)          | Retrieve the filedescriptor linked to a connection            |
| [MQ_send()](mq_send)                              | Send data over a SMTP connection                              |
| [MQ_authenticated()](mq_authenticated)            | Returns whether this is an authenticated connection           |
| [MQ_setAuthenticated()](mq_setauthenticated)      | Mark a connection as an authenticated connection              |
| [MQ_secure()](mq_secure)                          | Returns whether this is a secure TLS connection               |
| [MQ_connectionData()](mq_data)                    | Retrieve the data that is associated with the SMTP connection |
| [MQ_setConnectionData()](mq_setconnectiondata)    | Associated data with the SMTP connection                      |
