&lt;script src=&quot;https://aframe.io/releases/1.6.0/aframe.min.js&quot;&gt;&lt;/script&gt;
     &lt;script src=&quot;https://c-frame.github.io/aframe-physics-system/dist/aframe-physics-
system.js&quot;&gt;&lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
        &lt;a-scene id=&quot;s1&quot; fog=&quot;color: silver; near: 0&quot; animation=&quot;property: fog.far; to: 5; dur:
50000; easing: easeOutQuad&quot;&gt; 
             &lt;a-plane static-body width=&quot;40&quot; height=&quot;8&quot; position=&quot;-20 4 0&quot; rotation=&quot;0 0 0&quot;&gt;
                  &lt;a-box id=&quot;window&quot; color=&quot;silver&quot; opacity=&quot;0.5&quot; scale=&quot;1.25 1.25 0.5&quot; position=&quot;-
15 2 -0.2′′
                        sound=&quot;src: url(mixkit-glass-break-with-hammer-thud-759.wav)&quot;&gt;
                             &lt;a-light distance=&quot;1&quot; type=&quot;spot&quot; position=&quot;0 e 1&quot;&gt;&lt;/a-light&gt;
                             &lt;a-light angle=&quot;90&quot; intensity=&quot;0.01&quot; type=&quot;spot&quot; position=&quot;0 0 -1&quot;
rotation=&quot;180 0 0&quot;&gt;&lt;/a-light&gt; 
                       &lt;/a-box&gt;
&lt;/a-plane&gt;
&lt;a-plane static-body width=&quot;40&quot; height=&quot;8&quot; position=&quot;20 4 0&quot; rotation=&quot;e -90 0&quot;&gt;&lt;/a-
plane&gt; 
&lt;a-plane static-body width=&quot;40&quot; height=&quot;8&quot; position=&quot;0 4 20&quot; material-&quot;side:back&quot;&gt;&lt;/a-
plane&gt; 
&lt;a-plane static-body width=&quot;40&quot; height=&quot;8&quot; position=&quot;0 4 -20&quot;&gt;&lt;/a-plane&gt;
&lt;a-plane static-body width=&quot;40&quot; height=&quot;40&quot; position=&quot;0 0 0&quot; rotation=&quot;-90 0 0&quot;&gt;&lt;/a-
plane&gt; 
&lt;a-plane static-body width=&quot;40&quot; height=&quot;40&quot; position=&quot;0 8 0&quot; rotation=&quot;90 0 0&quot;&gt;&lt;/a-plane&gt;
&lt;a-plane id=&quot;door&quot; height=&quot;4&quot; width=&quot;2&quot; color=&quot;darkgreen&quot; position=&quot;0 2 -19.9&quot;
sound=&quot;src: url(mixkit-locking-a-shop-door-with-keys-202.wav)&quot;&gt; 
       &lt;a-ring color=&quot;black&quot; radius-inner-&quot;0.01&quot; radius-outer= &quot;0.1&quot; position=&quot;0.75 0 0.01&quot;&gt;&lt;/a-
ring&gt;
&lt;/a-plane&gt;
&lt;a-camera id=&quot;cam&quot;&gt;
      &lt;a-text value=&quot;&quot; align=&quot;center&quot; geometry=&quot;primitive: plane; width: 0; height: 1&quot;
position=&quot;0 0.5 -1&quot; material=&quot;opacity: 0&quot;&gt;&lt;/a-text&gt; 
      &lt;a-cone static-body height=&quot;2&quot; position=&quot;0 -1 0&quot;&gt;&lt;/a-cone&gt;
      &lt;a-cursor color=&quot;yellow&quot; fuse=&quot;true&quot; far=&quot;10&quot;&gt;&lt;/a-cursor&gt;
      &lt;a-light id=&quot;light&quot; distance=&quot;20&quot; intensity=&quot;0.25&quot; type=&quot;spot&quot; penumbra=&quot;0.5&quot;
visible=&quot;false&quot;&gt;&lt;/a-light&gt; 
&lt;/a-camera&gt;

&lt;script&gt;

var locked = true, tool = false, gas = true, message = &quot;&quot;, time = 5000,
AFRAME.registerComponent(&#39;updating&#39;, {
       tick: function () {
if (gas) time--;
if (time &lt; 0) message = &quot;Game over...&quot;;
if (message != &quot;&quot;) this.el.setAttribute(&#39;value&#39;, message);
else this.el.setAttribute(&#39;value&#39;, &#39; &#39; + Math.round(time / 100));

var pos = document.getElementById(&#39;cam&#39;).getAttribute(&#39;position&#39;);
if (pos.x &lt; -19) pos.x = -19;
if (pos.x &gt; 19) pos.x = 19; 
if (pos.z&lt;-19) pos.z = -19; 
if (pos.z &gt; 19) pos.z = 19;
document.getElementById(&#39;cam&#39;).setAttribute(&#39;position&#39;, pos);
    }
});

για τα σύνθετα αντικείμενα:
&lt;a-cylinder dynamic-body id=&quot;hammer&quot; color=&quot;tan&quot; height=&quot;0.5&quot; radius=&quot;0.05&quot; focusing&gt;
&lt;a-box color=&quot;black&quot; width=&quot;0.5&quot; height=&quot;0.1&quot; depth=&quot;0.1&quot; position=&quot;0 0.25 0&quot;&gt;&lt;/a-box&gt;
&lt;/a-cylinder&gt;
&lt;a-cylinder dynamic-body id=&quot;key&quot; color=&quot;silver&quot; height=&quot;0.15&quot; radius=&quot;0.01&quot; focusing&gt;
&lt;a-box color=&quot;silver&quot; scale=&quot;0.04 0.03 0.02&quot; position=&quot;0.02 0.04 0&quot;&gt;&lt;/a-box&gt;
&lt;a-torus color=&quot;silver&quot; radius=&quot;0.03&quot; radius-tubular=&quot;0.003&quot; position=&quot;0 -0.1 0&quot;&gt;&lt;/a-torus&gt;
&lt;/a-cylinder&gt;
&lt;a-cylinder dynamic-body id=&quot;torch&quot; height=&quot;0.5&quot; radius=&quot;0.1&quot; rotation=&quot;900&quot; focusing&gt;
&lt;a-cone height=&quot;0.2&quot; radius-top=&quot;0.1&quot; radius-bottom=&quot;0.2&quot; position=&quot;0 0.2 0&quot;
rotation=&quot;180 0 0&quot;&gt;&lt;/a-cone&gt; &lt;a-light distance=&quot;20&quot; intensity=&quot;0.25&quot; type=&quot;spot&quot;
penumbra=&quot;0.5&quot; position=&quot;0 0.2 0&quot; rotation=&quot;90 e e&quot;&gt;&lt;/a-light&gt;
&lt;a-light distance=&quot;0.3&quot; type=&quot;spot&quot; position=&quot;0 0.4 0&quot; rotation=&quot;-90 e e&quot;&gt;&lt;/a-light&gt; &lt;/a-
cylinder&gt;
&lt;a-box dynamic-body id=&quot;table&quot; color=&quot;brown&quot; scale=&quot;3 0.2 3&quot; position=&quot;-10 2 -10&quot;&gt; &lt;a-
cylinder height=&quot;6&quot; radius=&quot;0.03&quot; position=&quot;-0.4 -3 -0.4&quot;&gt;&lt;/a-cylinder&gt; &lt;a-cylinder
height=&quot;6&quot; radius=&quot;0.03&quot; position=&quot;-0.4 -3 0.4&quot;&gt;&lt;/a-cylinder&gt;
&lt;a-cylinder height=&quot;6&quot; radius=&quot;0.03&quot; position=&quot;0.4 -3 -0.4&quot;&gt;&lt;/a-cylinder&gt; &lt;a-cylinder
height=&quot;6&quot; radius=&quot;0.03&quot; position=&quot;0.4 -3 0.4&quot;&gt;&lt;/a-cylinder&gt;
&lt;/a-box&gt;
&lt;a-box dynamic-body id=&quot;chair&quot; color=&quot;brown&quot; scale=&quot;1 0.1 1&quot; position=&quot;10 1.5 10&quot;&gt; &lt;a-
cylinder height=&quot;8&quot; radius=&quot;0.05&quot; position=&quot;-0.4 -4 -0.4&quot;&gt;&lt;/a-cylinder&gt; &lt;a-cylinder

height=&quot;8&quot; radius=&quot;0.05&quot; position=&quot;-0.4 -4 0.4&quot;&gt;&lt;/a-cylinder&gt; &lt;a-cylinder height=&quot;19&quot;
radius=&quot;0.05&quot; position=&quot;0.4 2 -0.4&quot;&gt;&lt;/a-cylinder&gt; &lt;a-cylinder height=&quot;19&quot; radius=&quot;0.05&quot;
position=&quot;0.4 2 0.4&quot;&gt;&lt;/a-cylinder&gt; &lt;a-box color=&quot;silver&quot; scale=&quot;0.05 5 1&quot; position=&quot;0.4 8
0&quot;&gt;&lt;/a-box&gt; &lt;/a-box&gt;
&lt;/script&gt;

&lt;script&gt;
var scene1 = document.getElementById(&#39;s1&#39;);
for (var i = 0; i &lt; 10; i++) {
     var t = document.getElementById(&#39;table&#39;).cloneNode(true);
     var x = Math.random() *40 20;
     var z Math.random() *40 - 20;
t.setAttribute(&#39;position&#39;, x + &#39; 2 &#39; + z);
t.setAttribute(&#39;rotation&#39;, &#39;0&#39;+ Math.random() * 90+ &#39;0&#39;);
scene1.appendChild(t);
}
for (var i = 0; i &lt; 20; i++) {
      var c= document.getElementById(&#39;chair&#39;).cloneNode(true);
      var x Math.random()* 40 20;
      var z = Math.random() *40 20;
c.setAttribute(&#39;position&#39;, x + &#39; 6&#39; + Z);
scene1.appendChild(c);
}
document.getElementById(&#39;hammer&#39;).setAttribute(&#39;position&#39;, (Math.random() *30 - 15) + &#39;5&#39;
+ (Math.random() *30 - 15));
document.getElementById(&#39;torch&#39;).setAttribute(&#39;position&#39;, (Math.random()* 30 - 15) + &#39; 3 &#39; +
(Math.random() * 30 - 15));
document.getElementById(&#39;key&#39;).setAttribute(&#39;position&#39;, (Math.random() + &#39;1&#39; +
(Math.random() * 30 - 15));
&lt;/script&gt;

AFRAME.registerComponent(&#39;focusing&#39;, {
     init: function () {
           var el = this.el;
         el.addEventListener(&#39;mouseenter&#39;, function () {
                var pos = document.getElementById(&#39;cam&#39;).getAttribute(&#39;position&#39;);

      if (el.id = &quot;door&quot;) {

           if (!locked &amp;&amp; time &gt;= 0) { el.components.sound.playSound(); message = &quot;Well done &quot;;
}
           return;
}
else if (el.id == &quot;window&quot;) {
         if (tool) {
         document.querySelector(&#39;a-scene&#39;).removeAttribute(&#39;animation&#39;);
         document.querySelector(&#39;a-scene&#39;).setAttribute(&#39;animation&#39;, &#39;property: fog.far; to:
1000; dur: 50000&#39;);
         gas = false;
         el.components.sound.playSound(); el.setAttribute(&#39;blending&#39;, &#39;subtractive&#39;);
     }
     return;
}
el.removeAttribute(&#39;dynamic-body&quot;);
el.setAttribute(&#39;animation&#39;, &#39;property: position; to: &#39; + pos.x + &#39; 0 &#39; + pos.z);

if (el.id == &quot;torch&quot;) document.getElementById(&#39;light&#39;).setAttribute(&#39;animation&#39;, &#39;property:
visible; to: true&#39;); 
else if (el.id &quot;key&quot;) locked = false;
else if (el.id == &quot;hammer&quot;) tool = true;
setTimeout(function () { el.remove(); }, 3000);
});
}
});
