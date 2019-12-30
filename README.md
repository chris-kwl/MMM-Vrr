# MMM-Vrr and more Areas

This is a module for the [MagicMirror²](https://github.com/MichMich/MagicMirror/).

Displays the next departure times of Trains, subway and Buses from any city and station in the [below](#efa) mentioned areas (by transportation authorities). By default only in the VRR-Area (basically North Rhine-Westphalia) and some other stations in the DACH countries. See [Support for other Areas](#efa).


![displayType detail](mmm-vrr-table.png) &nbsp;&nbsp; ![displayType digital](mmm-vrr.png)


## Installation

1. Navigate into your MagicMirror's `modules` folder.
1. Execute `git clone https://github.com/Klizzy/MMM-Vrr.git`.
1. Execute `cd MMM-Vrr`.
1. Execute `npm install`.

## Using the module

To use this module, add the following configuration block to the modules array in the `config/config.js` file:
```
{
    module: 'MMM-Vrr',
    position: "top_right",
    config: {
        city: 'Düsseldorf',
        station: 'Hauptbahnhof',
        numberOfResults: 10,
        displayTimeOption: 'countdown',
        displayType: 'detail'
    }
}  
```

## Using the module with differend backend

If the desired station is not found with the VRR backend, use the secific backend of the area (see [List](#efa) below).
The names of the stations differ depending on the backend, to find the right combination of city and station see https://vrrf.finalrewind.org/ (GUI of the used 3rd Party API).

```
{
    module: 'MMM-Vrr',
    position: "top_right",
    config: {
        //city: 'Bremen', // For HEFAS Backends not needed
        station: 'Rembertistraße', // Station in Bremen (VBN Area)
        backend: 'hafas.VBN', // Backend of the VBN (Verkehrsverbund Bremen/Niedersachsen)
        numberOfResults: 10,
        displayTimeOption: 'countdown',
        displayType: 'lcd'
    }
}  
```

## Configuration options

| Option           | Description | Options |
|----------------- |---|---
| `city`           | *Required* German City Name <br><br>**Type:** `String` (**default**: Düsseldorf) | Any City Name in North Rhine-Westphalia
| `station`        | *Required* German Station Name <br><br>**Type:** `String` (**default**: Hauptbahnhof) | Any Station Name in North Rhine-Westphalia
| `numberOfResults`| *Optional* Number of results to be displayed <br><br>**Type:** `Int` (**default**: 10) | *
| `displayType`| *Optional* Changes the display type <br><br>**Type:** `String` (**default**: 'detail') | `'detail'`, `'lcd'`
| `displayIcons`   | *Optional* Display fontawsome icons <br><br>**Type:** `boolean` (**default**: true) | `false`
| `updateInterval` | *Optional* Sets the Update Interval int <br><br>**Type:** `int`(milliseconds) <br> **Default** 60000 milliseconds (1 minute) | * (API result is always cached for 1 Min)
| `displayTimeOption` | *Optional* Changes the type of time <br><br>**Type:** `String` (**default**: 'countdown') | `'time'`, `'time+countdown'`, `'countdown'`
| `setWidth`| *Optional* Sets the width of the module in pixel <br><br>**Type:** `int` (**default**: false) | Any posible size like: `450`
| `lcdWidth` | *Optional* Sets the width of the lcd display type <br><br>**Type:** `int` (**default**: 450) | any possible size
| `scrollAfter` | *Optional* Scrolls the destination text after the specified characters <br><br>**Type:** `int` (**default**: false) | any possible size or `false`
| `line` | *Optional* Only show lines that start with the given string. Supports multiple strings, separated by comma (","). <br><br>**Type:** `string` (**default**: empty (i.e., show all lines)) | any possible string (e.g., "RB33,U")
| `backend`        | *Optional* Set another Backend (default/emty = VRR). Makes the other areas fully supported, by select the specifc area-backend <br><br>**Type:** `String` (**default**: emty) | Any Backend in the [List](#efa) below.

## Supported Languages

Currently only `de` and `en` is supported. Gets the Value from the Global Magic Mirror language config.

## "LCD" Display

![lcd](mmm-vrr.png)</br>
This option can be set if ```displayType: 'lcd'``` is added. Here, no delays, icons or absolute times are shown.


## Visualization of the scrollAfter option

If you set `scrollAfter:15`, the text will be scrolled horizontally if it has 15 or more characters.

![Auto scroll](scrollAfter.gif)

## <a name="efa"></a>Support for other Areas

This module was intended for VRR, but it also supports the following Areas.
Possible Side effects for not VRR Areas:
* Icons don't match correctly
* not all configured transport types hide correctly

**Areas and specific Backend:**
* ASEAG `ura.ASEAG`
* BSVG `efa.BSVG`
* BVG `hafas.BVG`
* DB `hafas.DB`
* DING `efa.DING`
* IVB `efa.IVB`
* KVV `efa.KVV`
* LinzAG `efa.LinzAG`
* MM `ura.MM`
* NAHSH `hafas.NAHSH`
* NASA `hafas.NASA`
* NVBW `efa.NVBW`
* NVV `hafas.NVV`
* ÖBB `hafas.ÖBB`
* RSAG `hafas.RSAG`
* SBB `hafas.SBB`
* SVV `efa.SVV`
* TfL `ura.TfL`
* TLEM `efa.TLEM`
* VBB `hafas.VBB`
* VBL `efa.VBL`
* VBN `hafas.VBN`
* VGN `efa.VGN`
* VMV `efa.VMV`
* VOR `efa.VOR`
* VRN `efa.VRN`
* VRNdelfi `efa.VRNdelfi`
* VRR `efa.VRR`
* VRR2 `efa.VRR2`
* VVO `efa.VVO`
* VVS `efa.VVS`
* VVV `efa.VVV`



## Feedback

Its my first Open Source Project, so it would be nice if you share your experience with this module with me <a href="mailto:steven.zemelka@gmail.com">steven.zemelka@gmail.com</a>!
Feel free to suggest additional features and / or improvements. 

## Changelog

#### Version 1.0

* initial release

#### Version 1.1

* added some additional configuration to set a custom width
* added the option to scroll the destination text horizontally

#### Version 1.2

* now displays delays

#### Version 1.5

* delay bugfix and styling changes
* rail track is now displayed
* added additional display type

#### Version 1.5.1

* fix for Issue #3 scrollAfter and displayType lcd

#### Version 1.6

* shown lines can now be filtered and code improvements. THX @wapolinar !
* added `contributing.md` 
