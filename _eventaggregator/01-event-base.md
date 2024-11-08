---
title: "Event Base"
permalink: /eventaggregator/event-base/
layout: single
author_profile: false
toc: true
---

**Event Base** (`UEventBase` in C++) derives from `UObject` and serves as the foundational class for defining
events in the **Event Aggregator** plugin. It is intended for extension by project-specific event classes, each subclass
uniquely representing an event or gameplay interaction within the system.

This class is also meant to be utilized as a payload when broadcasting events via the **Event Aggregator Subsystem**.
By using `UEventBase` as a base class for event payloads, developers can take advantage of type-safe casting when handling
and processing specific event types.


## UEventBase in C++

{% highlight c++ %}

UCLASS(BlueprintType, Blueprintable)
class EVENTAGGREGATOR_API UEventBase : public UObject

{% endhighlight %}

It is recommended that developers inherit from this base class, with each subclass defining a unique gameplay event.

## UEventBase in Blueprints

Blueprint developers can also utilize `UEventBase` as a foundation for creating their own **'Event Class Blueprints'**.

It supports editor integration, allowing new events to be created directly from the context menu in the Content Browser.

## Binding Information

This class also contains binding information to facilitate debugging, including details like the object bound to the event and the name of the associated function.

It achieves this via a `USTRUCT` called `FEventBindingInfo` which holds the name of the bound object and its associated function.