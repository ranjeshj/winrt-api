---
-api-id: E:Windows.UI.Xaml.UIElement.PointerMoved
-api-type: winrt event
---

<!-- Event syntax
public event Windows.UI.Xaml.Input.PointerEventHandler PointerMoved
-->

# Windows.UI.Xaml.UIElement.PointerMoved

## -description

Occurs when a pointer moves while the pointer remains within the hit test area of this element.

## -xaml-syntax

```xaml
<uiElement PointerMoved="eventhandler"/>
```

## -remarks

Touch, mouse, and pen/stylus interactions are received, processed, and managed as pointer input in UWP app. Any of these interactions can produce a PointerMoved event. For more info, see [Handle pointer input](https://docs.microsoft.com/windows/uwp/input-and-devices/handle-pointer-input) and the "PointerMoved for mouse and stylus input" section of this topic.

In some UI scenarios, particularly if the user is using a mouse, this event will fire a lot. Be aware of the performance profile for code you put into this handler, and consider ways to use your own flags or tolerances that can throttle how many times the logic actually needs to run.

This event is a routed event. For more info on the routed event concept, see [Events and routed events overview](https://docs.microsoft.com/windows/uwp/xaml-platform/events-and-routed-events-overview).

For touch actions and also for interaction-specific or manipulation events that are consequences of a touch action, an element must be hit-test visible in order to be the event source and fire the event that is associated with the action. [UIElement.Visibility](uielement_visibility.md) must be [Visible](visibility.md). Other properties of derived types also affect hit-test visibility. For more info, see [Events and routed events overview](https://docs.microsoft.com/windows/uwp/xaml-platform/events-and-routed-events-overview).

This event also supports the ability to attach event handlers to the route that will be invoked even if the event data for the event is marked **Handled**. See [AddHandler](uielement_addhandler_2121467075.md).

### PointerMoved for mouse and stylus input

A mouse input device has an onscreen cursor that is visible whenever the mouse moves over an element's bounds, even if no mouse button is pressed at the time. Similar behavior is available for pen device input, where the input devices can detect that the pen is hovering just over the input device surface but not touching it. Mouse and pen input will thus fire PointerMoved events more often than touch input. For more info, see [Mouse interactions](https://docs.microsoft.com/windows/uwp/input-and-devices/mouse-interactions).

In contrast, a touch point is only detectable if a finger is touching the surface. A touch point will generate PointerMoved only while that touch point remains in constant contact with the surface as it moves. For these kinds of touch actions that are generating PointerMoved it's also likely that the action will be processed as a manipulation, or as a gesture. For more info, see [Handle pointer input](https://docs.microsoft.com/windows/uwp/design/input/handle-pointer-input).

Mouse input is associated with a single pointer assigned when mouse input is first detected, and all mouse-initiated interactions have the same [PointerId](../windows.ui.input/pointerpoint_pointerid.md). Clicking a mouse button (left, wheel, or right) creates a secondary association between the pointer and that button through the [PointerPressed](uielement_pointerpressed.md) event. The [PointerReleased](uielement_pointerreleased.md) event is fired only when that same mouse button is released (no other button can be associated with the pointer until this event is complete). Because of this exclusive association, other mouse button clicks are routed through the PointerMoved event. You can test the mouse button state when handling this event, as shown in this example:

[!code-csharp[PointerMoved](../windows.ui.input.inking/code/PointerInput/csharp/MainPage.xaml.cs#SnippetPointerMoved)]

[!code-csharp[PointerMoved](../windows.ui.input.inking/code/PointerInput_UWP/csharp/MainPage.xaml.cs#SnippetPointerMoved)]

## -examples

## -see-also

[PointerRoutedEventArgs](../windows.ui.xaml.input/pointerroutedeventargs.md), [PointerEntered](uielement_pointerentered.md), [OnPointerMoved](../windows.ui.xaml.controls/control_onpointermoved_600528909.md), [Handle pointer input](https://docs.microsoft.com/windows/uwp/design/input/handle-pointer-input), [Handle pointer input](https://docs.microsoft.com/windows/uwp/input-and-devices/handle-pointer-input), [XAML user input events sample](https://go.microsoft.com/fwlink/p/?linkid=231524)
soft.com/fwlink/p/?linkid=231524)
