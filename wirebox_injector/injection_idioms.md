# Injection Idioms

Now that we have constructed our injector let's discuss a little about injection idioms or styles WireBox offers before we go all cowboy and start configuring and using this puppy. Below is a nice chart that showcases the WireBox injection styles, but we really encourage you to review our dependency injection section to learn the different approaches to DI, their values, and when to use them.

<table>
    <tr>
        <th></th>
        <th></th>
        <th></th>
        <th></th>
    </tr>
    <tr>
        <td>Constructor</td>
        <td>First</td>
        <td>Mandatory dependencies for object creation </td>
        <td>Each constructor argument receives a inject annotation with its required injection DSL. Be careful when dealing with object circular dependencies as they will fail via constructor injection due to its chicken and the egg nature.</td>
    </tr>
    <tr>
        <td>CFProperty</td>
        <td>Second</td>
        <td>Great documentable approach to variable mixins to reduce getter/setter verbosity </td>
        <td>Leverages the greatest aspect of ColdFusion, dynamic language, to mixin variables at runtime by using the cfproperty annotations. Great for documentation and visualizing object dependencies and safe for circular dependencies. Cons is that you can not use the dependencies in an object's constructor method. </td>
    </tr>
    <tr>
        <td>Setter Methods</td>
        <td>Third</td>
        <td>Legacy classes </td>
        <td>The inject annotation MUST exist on the setter method if the object is not mapped. Mapping must be done if you do not have access to the source or you do not want to touch the source.</td>
    </tr>
</table>

These are the three injection styles that WireBox supports and which style you choose depends on your requirements and also your personal taste. The setter method approach is linked to the way Spring and ColdSpring approach it which is the traditional JavaBean style of setXXX where XXX is the name of the mapping or object to pass into the setter method for injection.
<div style="border: 1px solid black">
<img src="../images/icon_info.png" width="12%" style="float:left;margin-top:10px"><p style="margin:12px"><b>
Note: Whichever injection style you use with WireBox, the target's visibility does not matter. This means that you can create private or package methods and WireBox will still inject them for you. This is absolutely great when you are an encapsulation freak and you do not want to expose public setter methods.</b></p>
<div style="clear:both"></div>
</div>
<br>