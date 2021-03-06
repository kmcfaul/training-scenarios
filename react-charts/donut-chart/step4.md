Add a legend to the donut chart.

1) <strong>Make sure the `App.js` file is still open.</strong>

2) <strong>Locate the code for the `<ChartDonut>` component.</strong>

It should look like this:

<pre class="file">
&lt;ChartDonut
  data={[{ x: &#39;Cats&#39;, y: 35 }, { x: &#39;Dogs&#39;, y: 55 }, { x: &#39;Birds&#39;, y: 10 }]}
  subTitle=&quot;Pets&quot;
  title=&quot;100&quot;
  height={230}
  width={350}
  constrainToVisibleArea
  labels={({ datum }) =&gt; `${datum.name}: ${datum.y}%`}
/&gt;
</pre>

3) <strong>Add a `padding` property to the `<ChartDonut>` component.</strong>

This `padding` property adds more padding to accommodate the legend.

Copy this code to the editor:

<pre class="file" data-target="clipboard">
padding={{
  bottom: 20,
  left: 20,
  right: 140,
  top: 20
}}
</pre>


4) <strong>Add the `legendOrientation` property to the `<ChartDonut>` component.</strong>

Set the orientation for the `legendData` so that it behaves as expected when added in step 6 (there will be no visible changes yet).

The `legendOrientation` property specifies whether the legend is rendered horizontally or vertically. In this case it should be set to vertical:

<pre class="file" data-target="clipboard">
legendOrientation=&quot;vertical&quot;
</pre>

5) <strong>Add the `legendPosition` property to the `<ChartDonut>` component.</strong>

Set the position for the `legendData` so that it behaves as expected when added in step 6 (there will still be no visible changes yet).

The `legendPosition` property specifies whether the legend is rendered on the bottom or right of the chart. It should look like the following:

<pre class="file" data-target="clipboard">
legendPosition=&quot;right&quot;
</pre>

6) <strong>Add the `legendData` property to the `<ChartDonut>` component.</strong>

Inside the `legendData` should be an object with names for the data. It should look like the following:

<pre class="file" data-target="clipboard">
legendData={[
  { name: &#39;Cats&#39; }, 
  { name: &#39;Dogs&#39; }, 
  { name: &#39;Birds&#39; }, 
  { name: &#39;Mice&#39; }
]}
</pre>

Once the preview reloads, it should look like this:
<img src="donut-chart/assets/legend.png" alt="Chart with legend" style="box-shadow: rgba(3, 3, 3, 0.2) 0px 1.25px 2.5px 0px;" />

