# CrossRoad Core

The CrossRoad Project is meant to create some apps that will enable a secure server to server communication.

This is based on several security standards such as : 

* PCI DSS
* 3DSecure
* And others to come...

# Core App 

The Core App is meant to be the communicating part of the project.

This includes the **message's dispatcher**, the **message's creator API** and the **message reader**.

Let's see how this works...

## Message's Dispatcher

The point of the **Message's Dispatcher** is simply to move data on its hard drive. 

It will do so by following several naming rules on the messages' files' names. 

See an example here : 

```
DestinationServer_DestinationComponent_MessagePriority_<possibly-more-options>.crm
```
### DestinationServer :

Let the app knows :

*  Who can access this file,
*  Where it has to be distributed. 

### __DestinationComponent & MessagePriority :__

The server that access this file needs a little more information : 

*  The App or Component that will use this message. 
*  The Priority of the message.

This will allow to manage the way messages arrive on a server and direct them into the right service. 

In order to do so, Priority will be set-up on each message. 

## Message's Creator API 

In order to create useful messages, an API is required. 

Some key points are explained here : 

### 1. Security

Security is the foundation for this server to server communication app. As so, we must provide integrity to our messages.

**By default**, the API must: 

*  Provide issuing time,
*  Provide a validity period to the message (after this, the message won't be usable anymore),
*  Provide the issuer of the message (by name, or ID),
*  Provide an ID to the message (to be able to retrieve transactions),
*  Provide a possible encryption (if the data being transfered requires it, it must be done),
*  Provide the target (who can read the message).
*  Other needs will come later...

### 2. Reliability

In order to let the message useful, many fields are needed.

But, an API, by default, can't fit every needs. This is why it will need to :

* __Be dynamic by :__
1. Providing a field's creation (to be able to custom the API),
2. Providing different templates for some system actions.
* __Provide different running modes :__
1. Copying configuration files (it can happen that no commands are required, in that case, we simply setup configuration),
2. Performing actions (it might be shell actions that will work using scripts)
* __Provide an history of actions that have been done :__
1. In order to track actions,
2. Being able to undo a performed action (in case something goes wrong).
* __Provide a server dependency list (some servers need to work with some others) :__
1. Prevents from a service interuption (if the dependency is not up, all actions are postponed).



## Message's Reader

Servers need an agent that will be able to catch the sent messages, 

It will also allow them to give a feedback about the performed actions.

This agent needs to be as generic as possible, in order to take into account as much possibilities as possible.

Its job will mostly to consume the messages, by getting the actions ordered by it. 

Security checks will be performed locally in order to make sure that the requestor has permissions to run tasks on the machine.

