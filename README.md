<p align='center'>
  <b>WC3MapTranslator</b>
</p>
<p align='center'>
  Module to translate JSON map format to WC3 (war3map) files for .w3x<br/><br/>
  
  <a href='https://www.npmjs.com/package/wc3maptranslator'>
    <img src='https://img.shields.io/npm/dt/wc3maptranslator.svg?style=flat-square'/>
  </a>
  
  <a href='https://codeclimate.com/github/ChiefOfGxBxL/WC3MapTranslator'>
    <img src='https://img.shields.io/codeclimate/github/ChiefOfGxBxL/WC3MapTranslator.svg?style=flat-square'/>
  </a>
  
  <a href='https://opensource.org/licenses/MIT'>
    <img src='https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square'/>
  </a>
</p>
  
<hr/>
<p align='center'>
  <a href="#why"><strong>Why?</strong></a> &middot;
  <a href="#usage"><strong>Usage</strong></a> &middot;
  <a href="#file-support"><strong>File Support</strong></a> &middot;
  <a href="#specification"><strong>Specification</strong></a> &middot;
  <a href="#contributing"><strong>Contributing</strong></a> &middot;
  <a href="#special-thanks"><strong>Special Thanks</strong></a>
</p>
<hr/>

<br/>

### Why?
WC3MapTranslator is a module to convert a JSON representation of WarCraft III (.w3x) data to their `war3map` files. This module was created for use by Ice Sickle, the new-gen WC3 world editor. You are welcome to use this module for other projects.

*But still... why?* - You may wish to familiarize yourself with the Ice Sickle project. JSON is much easier for humans to read, compared to the byte format used by WC3 files. Of course, this does come with a trade-off: increased file size. But with increased storage today and cloud-hosting, this is no problem.

<br/>

### Usage
```js
var Translator = require('wc3maptranslator'),
    mapJson = { // Refer to "Specification"
        units: [...],
        doodads: [...],
        ...
    };

// Using individual translators, we may convert JSON
// representation to generate a WC3 .w3x map file.
// See the Wiki for more information.
var unitsTranslator = new Translator.Units(mapJson.units);
unitsTranslator.write(); // write output file (in this case, war3mapUnits.doo)
```

<br/>

### File Support

#### World files

| File              | Status      | Type          |
|-------------------|:-----------:|---------------|
| war3map.w3e       |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Terrain                 |
| war3mapUnits.doo  |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Units                   |
| war3map.doo       |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Doodads                 |
| war3map.w3r       |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Regions                 |
| war3map.w3c       |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Cameras                 |
| war3map.w3s       |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Sounds (definitions)    |

#### Object data files

| File            | Status      | Type          |
|-----------------|:-----------:|---------------|
| war3map.w3u     |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Units - Objects         |
| war3map.w3t     |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Items - Objects         |
| war3map.w3a     |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Abilities - Objects     |
| war3map.w3b     |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Destructables - Objects |
| war3map.w3d     |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Doodads - Objects       |
| war3map.w3q     |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Upgrades - Objects      |
| war3map.w3h     |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Buffs - Objects         |

#### Trigger files

| File            | Status      | Type          |
|-----------------|:-----------:|---------------|
| war3map.j       |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | JASS                    |
| war3map.wts     |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Strings                 |
| war3map.wtg     |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | JASS                    |
| war3map.wct     |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | JASS                    |


#### Map files

| File               | Status      | Type          |
|--------------------|:-----------:|---------------|
| war3map.w3i        |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Info File               |
| war3map.imp        |  ![check](https://cloud.githubusercontent.com/assets/4079034/25298706/7a881946-26c5-11e7-896b-402f60a0f059.png)   | Imported Files          |
| war3map.wpm        |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | Pathing                 |
| war3map.shd        |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | Shadow map              |
| war3map.mmp        |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | Menu Minimap            |
| war3mapMap.blp     |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | Minimap Image           |
| war3mapMap.b00     |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | Minimap Image (2)       |
| war3mapMap.tga     |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | Minimap Image (3)       |
| war3mapPreview.tga |  ![times](https://cloud.githubusercontent.com/assets/4079034/25298707/7a883642-26c5-11e7-841c-cd3eb1425461.png)   | Map Preview Image       |

<br/>

### Specification
We have an extensive [specification on our Wiki](https://github.com/ChiefOfGxBxL/WC3MapTranslator/wiki/Specification) explaining how to format a map in JSON. It explains everything from the high-level map object, all the way down to creating individual units, tiles, or custom objects.

The underlying WarCraft map files (e.g. war3map.doo) have been documented [on our Wiki](https://github.com/ChiefOfGxBxL/WC3MapTranslator/wiki) as well. If you are curious about how a .w3x file is composed, this is the place to learn!

<br/>

### Contributing
(Section pending)

<br/>

### Special Thanks
We owe a lot of thanks to *Chocobo* on [TheHelper](http://www.thehelper.net/) for the detailed documentation of the files found in a .w3x archive. Two tutorials are [here (1)](http://www.thehelper.net/threads/guide-explanation-of-w3m-and-w3x-files.35292/) and [here (2)](http://world-editor-tutorials.thehelper.net/cat_usersubmit.php?view=42787).
