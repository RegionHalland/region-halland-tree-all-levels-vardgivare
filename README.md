# Navigationsträd för vardgivare.regionhalland.se

## Hur man använder Region Hallands plugin "region-halland-tree-all-levels-vardgivare"

Nedan följer instruktioner hur du kan använda pluginet "region-halland-tree-all-levels-vardgivare".


## Användningsområde

Denna plugin skapar ett navigationsträd för vardgivare.regionhalland.se


## Installation och aktivering

```sh
A) Hämta pluginen via Git eller läs in det med Composer
B) Installera Region Hallands plugin i Wordpress plugin folder
C) Aktivera pluginet inifrån Wordpress admin
```


## Hämta hem pluginet via Git

```sh
git clone https://github.com/RegionHalland/region-halland-tree-all-levels-vardgivare.git
```


## Läs in pluginen via composer

Dessa två delar behöver du lägga in i din composer-fil

Repositories = var pluginen är lagrad, i detta fall på github

```sh
"repositories": [
  {
    "type": "vcs",
    "url": "https://github.com/RegionHalland/region-halland-tree-all-levels-vardgivare.git"
  },
],
```
Require = anger vilken version av pluginen du vill använda, i detta fall version 1.0.0

OBS! Justera så att du hämtar aktuell version.

```sh
"require": {
  "regionhalland/region-halland-tree-all-levels-vardgivare": "1.0.0"
},
```


## Loopa ut navigationsträdet via "Blade"

```sh
@if(function_exists('get_region_halland_tree_all_levels_vardgivare'))
  @php($myTree = get_region_halland_tree_all_levels_vardgivare())
  @foreach ($myTree as $tree1)
    <p>
      <a href="{{ $tree1['page_url'] }}">{{ $tree1['post_title'] }}</a>
      @if(count($tree1['children']) > 0)
          <span>TOOGLE</span>
      @endif
    <p>
    @foreach ($tree1['children'] as $tree2)
      <p class="ml1">
        <a href="{{ $tree2['page_url'] }}">{{ $tree2['post_title'] }}</a>
        @if(count($tree2['children']) > 0)
            <span>TOOGLE</span>
        @endif
      <p>
      @foreach ($tree2['children'] as $tree3)
        <p class="ml2">
          <a href="{{ $tree3['page_url'] }}">{{ $tree3['post_title'] }}</a>
        <p>
      @endforeach
    @endforeach
  @endforeach
@endif
```


## Versionhistorik

### 1.0.0
- Första version