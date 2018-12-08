# DOM Events
Client-side JavaScript programs use an asynchronous event-driven programming model.
In this style of programming, the web browser generates an event whenever something interesting happens
to the document or browser or to some element or object associated with it.
The event type is a string that specifies what kind of event occurred.

## MouseEvent
These event types belongs to the MouseEvent Object:

1. Click. The event occurs when the user clicks on an element
2. Contextmenu. The event occurs when the user right-clicks on an element to open a context menu
3. Dblclick. The event occurs when the user double-clicks on an element
4. Mousedown. The event occurs when the user presses a mouse button over an element
5. Mouseenter. The event occurs when the pointer is moved onto an element
6. Mouseleave. The event occurs when the pointer is moved out of an element
7. Mousemove. The event occurs when the pointer is moving while it is over an element
8. Mouseout. The event occurs when a user moves the mouse pointer out of an element, or out of one of its children
9. Mouseover. The event occurs when the pointer is moved onto an element, or onto one of its children
10. Mouseup. The event occurs when a user releases a mouse button over an element

## DragEvent

The DragEvent interface is a DOM event that represents a drag and drop interaction.
The user initiates a drag by placing a pointer device (such as a mouse) on the touch surface and then
dragging the pointer to a new location (such as another DOM element).

These event types belongs to the DragEvent Object:

1. Drag. This event is fired when an element or text selection is being dragged.
2. Dragend. This event is fired when a drag operation is being ended (by releasing a mouse button or hitting the escape key).
3. Dragenter. This event is fired when a dragged element or text selection enters a valid drop target.
4. Dragover. This event is fired continuously when an element or text selection is being dragged and the mouse pointer
is over a valid drop target (every 50 ms WHEN mouse is not moving ELSE much faster between 5 ms (slow movement) and 1ms
(fast movement) approximately. This firing pattern is different than mouseover ).
5. Dragleave. This event is fired when a dragged element or text selection leaves a valid drop target.
6. Dragstart. This event is fired when the user starts dragging an element or text selection.
7. Drop. This event is fired when an element or text selection is dropped on a valid drop target.

## KeyboardEvent

These event types belongs to the Keyboard Object:

1. Keydown. The keydown events happens when a key is pressed down;
2. Keyup. The keyup events happens when a key is released;
3. Keypress. The keypress events happens when a key is pressed down and then released;

### Auto-repeat

If a key is being pressed for a long enough time, it starts to repeat: the keydown triggers again and again,
and then when it’s released we finally get Keyup. So it’s kind of normal to have many keydown and a single keyup.
For all repeating keys the event object has event.repeat property set to true.

## TouchEvent

The TouchEvent interface represents an event sent when the state of contacts with a touch-sensitive surface changes.
This surface can be a touch screen or trackpad, for example. The event can describe one or more points of contact with
the screen and includes support for detecting movement, addition and removal of contact points, and so forth.
Touches are represented by the Touch object.

These event types belongs to the TouchEvent Object:

1. Touchstart.
Sent when the user places a touch point on the touch surface. The event's target will be the element in which the touch occurred.

2. Touchmove.
Sent when the user moves a touch point along the surface. The event's target is the same element that received the touchstart
event corresponding to the touch point, even if the touch point has moved outside that element.
This event is also sent if the values of the radius, rotation angle, or force attributes of a touch point change.

3. Touchend.
Sent when the user removes a touch point from the surface. This is also sent if the touch point moves off the edge of the surface;
for example, if the user's finger slides off the edge of the screen.
The event's target is the same element that received the touchstartevent corresponding to the touch point,
even if the touch point has moved outside that element.
The touch point (or points) that were removed from the surface can be found in the TouchList specified by the changedTouches attribute.

4. Touchcancel.
Sent when a touch point has been disrupted in some way. There are several possible reasons why this might happen
(and the exact reasons will vary from device to device, as well as browser to browser):
1.	An event of some kind occurred that canceled the touch; this might happen if a modal alert pops up during the interaction.
2.	The touch point has left the document window and moved into the browser's UI area, a plug-in, or other external content.
3.	The user has placed more touch points on the screen than can be supported, in which case the earliest Touch in the TouchList gets canceled.

## PointerEvent

To reduce the cost of coding to multiple input types and also to help with the above described ambiguity with Mouse Events,
this specifications defines a more abstract form of input, called a pointer. A pointer can be any point of contact
on the screen made by a mouse cursor, pen, touch (including multi-touch), or other pointing input device.
This model makes it easier to write sites and applications that work well no matter what hardware the user has.

These event types belongs to the PointerEvent Object:

1. Pointerover. A pointing device is moved into the hit test boundaries of an element.
2. Pointerenter. A pointing device is moved into the hit test boundaries of an element or one of its descendants,
including as a result of a pointerdown event from a device that does not support hover.
3. Pointerdown. A pointer enters the active buttons state.
4. Pointermove. A pointer changes coordinates.
5. Pointerup. A pointer leaves the active buttons state.
6. Pointercancel.
7. Pointerout.
8. Pointerleave. A pointing device is moved out of the hit test boundaries of an element and all of its descendants,
including as a result of a pointerup and pointercancel events from a device that does not support hover
9. Gotpointercapture. An element receives pointer capture.
10. Lostpointercapture. Pointer capture is released for a pointer.

## Another Events:

1. The FocusEvent interface represents focus-related events like focus, blur, focusin, or focusout.
2. The InputEvent interface represents an event notifying of editable content change.
3. The WheelEvent interface represents events that occur due to the user moving a mouse wheel or similar input device.

## Event object

An event object is an object that is associated with a particular event and contains details about that event.
Event objects are passed as an argument to the event handler function (except in IE8 and before where they are sometimes
only available through the global variable event). All event objects have a type property that specifies the event type and a target property that specifies the event target.
Each event type defines a set of properties for its associated event
object. The object associated with a mouse event includes the coordinates of the mouse pointer, for example,
and the object associated with a keyboard event contains details about the key that was pressed and the modifier keys that were held down.

## How to add the listener on the window object

The addEventListener method is the most preferred way to add an event listener to window, document or any other element in the DOM.

### addEventListener Example

```sh
document.addEventListener("click", myFunction);
document.addEventListener("click", someOtherFunction, true);
```

If the third argument is true, the event handler is registered as a capturing event handler for invocation during this first phase of event propagation.

There is one more way called “on” property onclick, onmouseover, and so on. But is not as useful,
as it does not allow us to add multiple event listeners on the same element.

### on prefix Example

```sh
window.onload = function() {
  alert(something happened);
};
```

An event object is passed as an argument (optional) to the handler which contains all the information related to the event (in our case, mousedown) on the window

## Event propagation

3 phases of event propagation
1. Capturing phase;
2. Target phase;
3. Bubbling phase.

Event propagation is the process by which the browser decides which objects to trigger event handlers on.
For events that are specific to a single object (such as the load event on the Window object), no propagation is required.
When certain kinds of events occur on document elements, however, they propagate or “bubble” up the document tree.
In another form of event propagation, known as event capturing, handlers specially
registered on container elements have the opportunity to intercept (or “capture”) events before they are delivered to their actual target.
Some events have default actions associated with them. When a click event occurs on a hyperlink, for example,
the default action is for the browser to follow the link and load a new page. Event handlers can prevent this default action
by returning an appropriate value, invoking a method of the event object, or by setting a property of the event object.
This is called “canceling” the event.

### Let’s see it in action:

```html
<form>
  <div>
    <p></p>
  </div>
</form>
```

If you click on "P", then the sequence is:

```sh
•	HTML → BODY → FORM → DIV → P (capturing phase), and then:
•	P → DIV → FORM → BODY → HTML (bubbling phase).
```

P shows up two times: at the end of capturing and at the start of bubbling.

An event handler can stop the propagation of an event, so that it will not continue to bubble and will not trigger handlers on containing elements.

How to prevent propagation?
	event.stopPropagation()

## Event delegation

It is sometimes more convenient to register a single event handler on a Document or other container element than to register handlers on each individual element you’re interested in.

### Event delegation example

```html
<ul> <!-- handle event on parent -->
  <li><a href="#">Item 1</a></li>
  <li><a href="#">Item 2</a></li>
  <li><a href="#">Item 3</a></li>
  <li><a href="#">Item 4</a></li>
</ul>
```

##  Thanks for attention