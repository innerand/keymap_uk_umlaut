# UK Keymap with German Umlauts
for virtual console and the X Keyboard Extension (XKB)
![Layout](https://raw.githubusercontent.com/innerand/keymap_uk_umlaut/master/keymap_uk_umlaut.png)

- Extends the gb (vconsole) and uk (xkb) keyboardmaps with German Umlauts
- Maps Escape to Caps (vim users)

## Usage
- Press *AltGr* and *a,o,u/A,O,U* to get Umlauts 
- Press *AltGr* and *Caps* to toggle Caps lock

## Setup
Both maps depend on the default gb/uk map.

### Virtual Console
Gzip and copy `uk-umlaut.map` to the keymaps location, activate it.

```
gzip uk-umlaut.map
cp uk-umlaut.map.gz /usr/share/kbd/keymaps/i386/qwerty/
localectl set-keymap uk-umlaut
```
(Example for ArchLinux)

### X Keyboard Extension (XKB)
#### User / Testing
- Copy `gb_uml` to `~/.xkb/symbols/`
- Get current configuration `setxkbmap -print > ~/.xkb/gb_uml.xkb`
- Edit `gb_uml.xkb` and add `gb_uml` to `xkb_symbols`

```
	xkb_keymap {
   	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
   	xkb_types     { include "complete"	};
	   xkb_compat    { include "complete"	};
   	xkb_symbols   { include "pc+gb_uml+gb:2+at(nodeadkeys):3+us:4+inet(evdev)"	};
   	xkb_geometry  { include "pc(pc105)"	};
   };
```
- Load configuration `xkbcomp -I$HOME/.xkb $HOME/.xkb/gb_uml.xkb $DISPLAY`

### System
- Copy `gb_uml` to `\usr\share\X11\xkb\symbols`
- Add layout to `base.xml` and `evdev.xml` (`\usr\share\X11\xkb\rules\`)

```xml
    <layout>
      <configItem>
        <name>gb_uml</name>
        <shortDescription>en</shortDescription>
        <description>English (UK,Umlauts)</description>
        <languageList>
          <iso639Id>eng</iso639Id>
        </languageList>
     </configItem>
    </layout>
```

## Copyright
[License](/LICENSE.md).


