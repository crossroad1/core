# CrossRoad Core

The CrossRoad Project is meant to create some apps that will enable a secure server to server communication.

This is based on several security standards such as : 

* PCI DSS
* 3DSecure
* And others to come...

## Core App 

The Core App is meant to be the communicating part of the project.

This includes the **message's dispatcher** and the **message's creator API**

Let's see how this works...

### Message's Dispatcher

The point of the **Message's Dispatcher** is simply to move data on its hard drive. 

It will do so by following several naming rules on the messages' files' names. 

See an example here : 

```
DestinationServer_DestinationComponent_MessagePriority_<possibly-more-options>.crm
```
#### DestinationServer :

Let the app knows :

*  Who can access this file,
*  Where it has to be distributed. 

#### __DestinationComponent & MessagePriority :__


The server that access this file needs a little more information : 

*  The App or Component that will use this message. 
*  The Priority of the message.

This will allow to manage the way messages arrives on a server. 

In order to do so, Priority will be set-up on each message. 

### Message's Creator API 

More to come...
