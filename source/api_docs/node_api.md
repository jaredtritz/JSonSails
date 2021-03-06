<a name="NodeApi"></a>

```eval_rst
.. _`NodeApi`:
```

## NodeApi
Interface to node objects. The current node object is accessed from `js.node`


* [NodeApi](#NodeApi)
    * [.children](#NodeApi+children)
    * [.dom](#NodeApi+dom)
    * [.id](#NodeApi+id)
    * [.parent](#NodeApi+parent)
    * [.title](#NodeApi+title)
    * [.call(method, params)](#NodeApi+call) ⇒ <code>promise</code>
    * [.evaluateLogic()](#NodeApi+evaluateLogic) ⇒ <code>boolean</code>
    * [.ready(callback)](#NodeApi+ready)
    * [.render()](#NodeApi+render) ⇒ [<code>NodeApi</code>](#NodeApi)
    * [.renderChildren(children)](#NodeApi+renderChildren)

<a name="NodeApi+children"></a>

```eval_rst
.. _`NodeApi+children`:
```

### js.node.children
<table>
  <thead>
    <tr>
      <th>Type</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td><code><a href="#NodeApi">array.&lt;NodeApi&gt;</a></code></td>
    </tr>  </tbody>
</table>

Array of child nodes once children have been rendered

<a name="NodeApi+dom"></a>

```eval_rst
.. _`NodeApi+dom`:
```

### js.node.dom
<table>
  <thead>
    <tr>
      <th>Type</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td><code>Element</code></td>
    </tr>  </tbody>
</table>

DOM element of this node's rendered HTML

<a name="NodeApi+id"></a>

```eval_rst
.. _`NodeApi+id`:
```

### js.node.id
<table>
  <thead>
    <tr>
      <th>Type</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td><code>string</code></td>
    </tr>  </tbody>
</table>

ID of this node, also given to id of HTML div tag wrapping this node

<a name="NodeApi+parent"></a>

```eval_rst
.. _`NodeApi+parent`:
```

### js.node.parent
<table>
  <thead>
    <tr>
      <th>Type</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td><code><a href="#NodeApi">NodeApi</a></code></td>
    </tr>  </tbody>
</table>

parent of this node, null for root node

<a name="NodeApi+title"></a>

```eval_rst
.. _`NodeApi+title`:
```

### js.node.title
<table>
  <thead>
    <tr>
      <th>Type</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td><code>string</code></td>
    </tr>  </tbody>
</table>

Title of this node, set from node property

<a name="NodeApi+call"></a>

```eval_rst
.. _`NodeApi+call`:
```

### js.node.call(method, params) ⇒ <code>promise</code>
<table>
  <thead>
    <tr>
      <th>Param</th><th>Type</th><th>Description</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td>method</td><td><code>string</code></td><td><p>method name to call on referenced module</p>
</td>
    </tr><tr>
    <td>params</td><td><code>*</code></td><td><p>parameters for the method</p>
</td>
    </tr>  </tbody>
</table>

Only works on ReferenceNodes. Initiate an async call to the module
behind the refnode. The method being called needs to be bound first on
the receiving module using `js.module.bind()`. Returns a Promise which
will be resolved with the method's return value.

<a name="NodeApi+evaluateLogic"></a>

```eval_rst
.. _`NodeApi+evaluateLogic`:
```

### js.node.evaluateLogic() ⇒ <code>boolean</code>
Run the logic script on this node. Used when implementing a custom
[renderChildren](#NodeApi+renderChildren) function, to
conditionally render child nodes.
Returns true or false, the result of this node's logic script.

<a name="NodeApi+ready"></a>

```eval_rst
.. _`NodeApi+ready`:
```

### js.node.ready(callback)
<table>
  <thead>
    <tr>
      <th>Param</th><th>Description</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td>callback</td><td><p>function to call when node has been rendered.</p>
</td>
    </tr>  </tbody>
</table>

Accepts a function that will get called when all descendants of this node have been
rendered. The function context `this` will be set to this node.

<a name="NodeApi+render"></a>

```eval_rst
.. _`NodeApi+render`:
```

### js.node.render() ⇒ [<code>NodeApi</code>](#NodeApi)
Method to render DOM of this node. Should only be called within the
renderChildren function. See
[renderChildren](#NodeApi+renderChildren) for example usage.

<a name="NodeApi+renderChildren"></a>

```eval_rst
.. _`NodeApi+renderChildren`:
```

### js.node.renderChildren(children)
Override this method to customize how children are rendered.  
<table>
  <thead>
    <tr>
      <th>Param</th><th>Type</th><th>Description</th>
    </tr>
  </thead>
  <tbody>
<tr>
    <td>children</td><td><code><a href="#NodeApi">NodeApi</a></code></td><td><p>array of child nodes</p>
</td>
    </tr>  </tbody>
</table>

This method is passed an array of child nodes which may be
rendered, the resulting child dom appended to `this.dom`. The array of
rendered children must be returned or else the children of the rendered
children will not be rendered.
This is the default function to use if not overridden:
```eval_rst
.. literalinclude:: ../comments/NodeApi.es6_render-children-method.js
    :language: javascript
```
See also:
- [render](#NodeApi+render)
- [evaluateLogic](#NodeApi+evaluateLogic)

