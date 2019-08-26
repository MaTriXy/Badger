![Icon](assets/icon.png) Badger
===============================
[![Build][1]][2]
[![Release][3]][4]
[![Versions][5]][6]
[![Arsenal][7]][8]


*Badger* is a generalized single purpose library for adding badges to drawables
in general and menu items in particular.

> **[sett]** (also **set**) - The earth or burrow of a badger.

Running with the Badger theme, it is all about the method `sett`. Home to the
badger, it is comprised of many tunnels and several entrances. It is the ideal
entry point to provide you with badges where mere drawables lived before.


Usage
-----

The `Badger.sett()` methods add a `BadgeDrawable` to the original drawable.
This results in a `LayerDrawable` with the `BadgeDrawable` added to the layer
with id `badger_drawable`. If the original drawable is a `LayerDrawable` having
a badge already set, this one gets reused instead.


#### Add a badge to a `MenuItem`

    BadgeDrawable badge = Badger.sett(menuItem, badgeFactory);

#### Add a badge to an `ImageView`

    BadgeDrawable badge = Badger.sett(imageView, badgeFactory);

#### Add a badge to a `Drawable`

    Badger<?> badger = Badger.sett(drawable, badgeFactory);
    BadgeDrawable badge = badger.badge;
    drawable = badger.drawable;

#### The `BadgeDrawable`

The BadgeDrawable implements handling of alpha values and color filters for a
default `Drawable`. *Badger* includes a general `TextBadge` with a single
purpose implementation `CountBadge`.


#### The `BadgeDrawable.Factory`

The type of the badge itself is determined by the implementation of the
`BadgeDrawable.Factory` supplied.

    public interface Factory<T extends BadgeDrawable> {
        T createBadge();
    }

The provided `BadgeDrawable` implementations define their own factories
`TextBadge.Factory` and `CountBadge.Factory`.


#### The `BadgeShape`

The `BadgeShape` is a simplified version of an Android `Shape` to be used with
`TextBadge`. With its `scale`, `aspectRatio` and `gravity` it defines the
actual size and position of the badge itself.

`BadgeShape` itself provides factories for *circle*, *square*, *oval*, *rect*,
*round-rect* and *round-square*.


![Example](assets/example.png)

    BadgeShape.oval(1f, 2f, Gravity.BOTTOM) // scale = 1 | aspectRatio = 2
    BadgeShape.square(1f, Gravity.NO_GRAVITY, .5f) // scale = 1 | radiusFactor = 0.5
    BadgeShape.circle(.5f, Gravity.END | Gravity.TOP) // scale = 0.5

#### scale
The `scale` determines the actual size of the badge drawable relative to the
size of the original drawable.

#### aspectRatio
The `aspectRatio` determines the actual shape of the badge itself. It is the
ratio between width and height. A value bigger than 1 makes the badge wider
than high, a value smaller than 1 makes it higher than wide.

#### gravity
The `gravity` determines the actual position of the badge inside the original
drawable. Layout directions are supported.

#### radiusFactor
The `radiusFactor` determines the actual radius of the circle, used to round the
corners of the rectangle, relative to the radius of the inner circle of the
badge.


Installation
------------

Add the updated dependency supporting _AndroidX_

    dependencies {
        implementation "com.github.v2rc:badger:$badgerVersion"
    }

or the legacy version supporting the _Support Library_

    dependencies {
        implementation 'berlin.volders:badger:0.2.1'
    }

Shortcomings
------------

The `TextBadge` only supports the RTL layout direction for Android Marshmallow
and later.

License
-------

    Copyright (C) 2016 Christian Schmitz
    Copyright (C) 2016 volders GmbH with <3 in Berlin

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
   
        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


  [sett]: https://en.oxforddictionaries.com/definition/sett
  [1]: https://travis-ci.org/v2rc/Badger.svg?branch=master
  [2]: https://travis-ci.org/v2rc/Badger
  [3]: https://jitpack.io/v/v2rc/badger.svg
  [4]: https://jitpack.io/#v2rc/badger
  [5]: https://asapi.herokuapp.com/com.github.v2rc/badger@svg
  [6]: https://asapi.herokuapp.com/com.github.v2rc/badger
  [7]: https://img.shields.io/badge/Android%20Arsenal-Badger-informational.svg
  [8]: https://android-arsenal.com/details/1/7811
