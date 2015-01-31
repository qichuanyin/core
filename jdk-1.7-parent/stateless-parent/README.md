WicketStuff Stateless
=====================================================

Sometimes it is good to be stateless. As the core of Wicket is focused on managing stateful behavior there is sometimes a lack of support for stateless pages. The goal of this package is to add a few components that provide more comprehensive stateless features for Apache Wicket.

These components currently include a ``StatelessLink``,a ``StatelessAjaxSubmitLink`` and  a ``StatelessAjaxFallbackLink``. They are backed by stateless behaviors: ``StatelessAjaxEventBehavior``, ``StatelessAjaxFormSubmitBehavior`` and ``StatelessAjaxFormComponentUpdatingBehavior``.

## Usage

Stateless components and behaviors follows the same rules and convetion of their standard stateful version shiped with Wicket. Therefore you will find different handler method like ``onSubmit`` or ``onClick`` that provide an instance of ``AjaxRequestTarget`` to refresh components markup. Such components must have a markup id in order to be manipulated via JavaScript. 

However, calling ``setOutputMarkupId``  on a component is not enough. Since we are working with a stateless page, the id of the component to refresh must be unique but also *static*, meaning that it should not depend on page instance. In other words, the id should be constant through different instances of the same page. 

By default Wicket generates markup ids using a session-level counter and this make them not static. Hence, to refresh component in a stateless page we must provide them with static ids, either setting them in Java code (with ``Component.setMarkupId``) or simply writing them directly in the markup.


##### Maven

This component is part of WicketStuff project and is regularly released at Maven Central repository. Simply add the following lines of configuration to our `pom.xml`:

````xml
<dependencies>
  <dependency>
    <groupId>org.wicketstuff</groupId>
    <artifactId>wicketstuff-stateless</artifactId>
    <version>6.8.0</version>
  </dependency>
</dependencies>
````