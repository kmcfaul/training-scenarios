Another customization option, available for all variants, is custom display and data for the Select options.

Let's begin with customizing the data. 

To change what data is passed around, and back to you on selection, you must implement a `SelectOptionObject` class. The only required property is a `toString` function, which converts whatever other data you include in the structure to a string format. This allows the component to internally compare options for filtering, and gives some limited customization for the option's display.

1) **Add `SelectOptionObject` to the list of imports from @patternfly/react-core.**

Your import statement should now look like this:
`import { Select, SelectOption, SelectVariant, SelectOptionObject } from "@patternfly/react-core";`

2) **Copy the following `CustomDataState` class, which extends `SelectOptionObject`, into the `App.js` file, outside of the App class:**

<pre class="file" data-target="clipboard">
  class CustomDataState implements SelectOptionObject {
    name: string;
    abbreviation: string;
    capital: string;
    founded: number;
    constructor(
      name: string,
      abbreviation: string,
      capital: string,
      founded: number
    ) {
      this.name = name;
      this.abbreviation = abbreviation;
      this.capital = capital;
      this.founded = founded;
    }
    toString = () =>
      `${this.name} (${this.abbreviation}) - Founded: ${this.founded}`;
  }
</pre>

<strong>Note:</strong> This class may contain any properties you wish to maintain as data when an option is selected. The `toString` function tells the select component how to display and compare the data as a string.

3) **Replace the state's `options` property, located in the App class constructor, with the following array that uses `CustomDataState`:**

<pre class="file" data-target="clipboard">
  options: [
    &lt;SelectOption
      value={new CustomDataState("Alabama", "AL", "Montgomery", 1846)}
    /&gt;,
    &lt;SelectOption
      value={new CustomDataState("Florida", "FL", "Tailahassee", 1845)}
    /&gt;,
    &lt;SelectOption
      value={new CustomDataState("New Jersey", "NJ", "Trenton", 1787)}
    /&gt;
  ]
</pre>

Currently, the `CustomDataState` is required `toString` function is used to display the data in the list. This allows for some limited customization in display, but if you want to use custom nodes, or separate data with display, you may use the children property of the `SelectOption`.

4) Edit the options state to display something different than the CustomDataState's toString.

<pre class="file" data-target="clipboard">
  options: [
    &lt;SelectOption
      value={new CustomDataState("Alabama", "AL", "Montgomery", 1846)}
    &gt;
      Alabama / AL
    &lt;/SelectOption&gt;,
    &lt;SelectOption
      value={new CustomDataState("Florida", "FL", "Tailahassee", 1845)}
    &gt;
      Florida / FL
    &lt;/SelectOption&gt;,
    &lt;SelectOption
      value={new CustomDataState("New Jersey", "NJ", "Trenton", 1787)}
    &gt;
      New Jersey / NJ
    &lt;/SelectOption&gt;
  ]
</pre>

Now, you should see these new values being displayed, and the filtering will match based on this display. In the case of html structures passed as a child, the component will convert the structure to a string for filtering.
//SCREENSHOT