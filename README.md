# Google Summer of Code 2019 - Work product summary

### Student Name
Prince Gupta (guptaprince8832@gmail.com)

### Organization
Videolan

### Project
VLC Desktop UI Improvement

### Mentors
Pierre Lamot, JB Kempf

## Overview

Videolan's VLC is a free and open source cross-platform multimedia player that plays most multimedia files as well as Blu-ray, DVD, Audio CD, VCD, and various streaming protocols. Many have revered it as best media player on desktop. VLC's desktop user interface is simple, flexible and lightweight. Though with time, its desktop interface has become old and outdated. However, the current development branch was under major redesign process, but the most important views was still not properly updated to match a modern user interface. My project aimed to overhaul the current media player and implement the new designs.


## Project

VLC's old desktop interface was developed using QtWidgets, though very simple, flexible and quite fast, it has become quite outdated and doesn't fit with new design paradigms of fluency and simplicity. At some point of time, it was decided to implement a whole new VLC desktop interface aimed to be simpler, modern, more user friendly and at the same time add a better "media center" feel into it. The plan was to use Qt's QML for frontend and C++ for backend. At the time when I started, a large portion of basic ground work was already done but almost all of main views was still outdated and was not properly following established design guidelines for the project. In this summer I worked on these views.

It was an excellent learning experience. A huge thanks to my mentors Pierre Lamot and JB Kempf. Their advice and experience have been truly invaluable and helpful throughout these past four months.

## Work

### [Patch 1](https://mailman.videolan.org/pipermail/vlc-devel/2020-June/134199.html)

GUI implementation at that time was following very loose and inconsistent spacing and layout sizes. So, my mentor Pierre introduced an idea to have common constants for width and margin, which can be used across GUI to assign such values. This patch implements that. I also added some premade widgets that can be used to add different types texts at different places in GUI.

### [Patch 2](https://mailman.videolan.org/pipermail/vlc-devel/2020-June/134285.html)

This patchset implemented a "PlayCover" widget that was used to highlight selected row's cover image in table view or selected cell's cover image in case of a grid type view. It displays a play icon which can be clicked to play the media. This patch also fixed oversized columns of Video table view.

### [Patch 3](https://mailman.videolan.org/pipermail/vlc-devel/2020-June/134332.html)

This patchset implemented special header and column delegates for duration type values. It adds an icon-based column header with centered aligned column texts. This also introduced required changes to different model implementations.

### [Patch 4](https://mailman.videolan.org/pipermail/vlc-devel/2020-June/134647.html)

This patchset aimed to redesign table-type views with following changes - add separators between rows, center aligns whole row in the main view, changes the position of section texts to align with following row, allow consumers of this type view to define their own delegates per column and add and use special delegates for title type column. Additionally, it also converted music genre view to table-based view from list based. 

### [Patch 5](https://mailman.videolan.org/pipermail/vlc-devel/2020-July/134997.html)

Next, I moved to working on grid type views. Starting with the base widget "GridItem" which is used as cell in all grid type view. I changed how GridItem layouts items and at the same time add shadows and animation to the same.

### [Patch 6](https://mailman.videolan.org/pipermail/vlc-devel/2020-July/135467.html)

Moving forward with working on grid type view, this patchset focused on overhauling different expand delegate implementations and their usage. Expand delegate occupies fixed height of Grid View and displays extra info about the selected item.


### [Patch 7](https://mailman.videolan.org/pipermail/vlc-devel/2020-August/135818.html)

The goal of this patchset was reimplementation of Music Artist View. Initially it was a single page with artist list at left side and their albums and songs at other. This patchset adds a new page at starting which contains only artists and then change view to more detailed view.

### [Patch 8](https://mailman.videolan.org/pipermail/vlc-devel/2020-August/135919.html)

This patch set focused on overhauling Music genre view. New way to generate genre cover was introduced.

### [Patch 9](https://mailman.videolan.org/pipermail/vlc-devel/2020-August/136271.html)

This patchset aimed to redo top bar's layout and appearance. It shifts button from top most bar to bar below it. Removes history next button. Updates Icons from designs. Adds shadows and animation. 

### [Patch 10](https://mailman.videolan.org/pipermail/vlc-devel/2020-August/136479.html)

This patchset focused on improving network view. Fixes spacing between items and added margins where applicable. Changes how cover images are loaded for network items, fixing oversized icons and improper coloring. I also converted existing list-type view to table type. 

### [Patch 11](https://mailman.videolan.org/pipermail/vlc-devel/2020-August/136491.html)

This patchset adds sticky section label in top headers of table view.

### [Patch 12](https://mailman.videolan.org/pipermail/vlc-devel/2020-August/136491.html)

This patchset makes artist list horizontally resizable. Also refactored playlist view to use same functionality.


## UI Changes
| Before      | After |
| ----------- | ----------- |  
![](screenshots/old_vlc.gif) | ![](screenshots/new_vlc.gif)


## Commits
All of my work got merged in VLC's main repository, following are the commits

 - [b846c65a98](https://code.videolan.org/videolan/vlc/-/commit/b846c65a985831dd439d0af5dbd4201610ddf2e1) qml: use HorizontalResizeHandle to make playlist horizontally resizable  
 - [21fc590caa](https://code.videolan.org/videolan/vlc/-/commit/21fc590caaaa9d920e44507bb4d2bf62fbee9531) qml: make artist list horizontally resizable  
 - [8ec81503ea](https://code.videolan.org/videolan/vlc/-/commit/8ec81503ea4a574d91a6b24cf9812e744baed994) qml: introduce HorizontalResizehandle  
 - [b4e4a65a65](https://code.videolan.org/videolan/vlc/-/commit/b4e4a65a65763f896492a956325de285abcff46e) qml: show 'Unknown Title' text when model value is unavailable in titleDelegate  
 - [0c0f914165](https://code.videolan.org/videolan/vlc/-/commit/0c0f914165e1831e56a7f518b1d49f7002c23c6f) qml: use ListLabel component for section labels of KeyNavigableTableView  
 - [c08f5767e6](https://code.videolan.org/videolan/vlc/-/commit/c08f5767e6e04f1bee83f9cc9c98e52d8afe3b44) qml: show top section of current view in header of KeyNavigableTableView  
 - [c601091efe](https://code.videolan.org/videolan/vlc/-/commit/c601091efe3052e3e29af950efc0a152ec026a3f) qml: add currentSection property to KeyNavigableListView  
 - [93dbbbdced](https://code.videolan.org/videolan/vlc/-/commit/93dbbbdced78a505ba1db6c2cecf96d78991af86) qml: correctly set cellHeight for grid items in NetworkBrowseDisplay  
 - [844586c38f](https://code.videolan.org/videolan/vlc/-/commit/844586c38feed4801daa40104f300e377ee8a725) qml: use SubtitleLabel for headers in NetworkBrowseDisplay  
 - [dda176f30b](https://code.videolan.org/videolan/vlc/-/commit/dda176f30bf6618b423d546fff723a24aec1a314) qml: implement play icon clicked for network grid items  
 - [3e49e4e371](https://code.videolan.org/videolan/vlc/-/commit/3e49e4e37102f0fedfaba2c590dab224f7fafcab) qml: use table view for list mode in NetworkBrowseDisplay  
 - [7d53a42c8a](https://code.videolan.org/videolan/vlc/-/commit/7d53a42c8ae8ed5e090ce9fd8193a463a1b4f1fc) qml: attach index property to column items of KeyNavigableTableView  
 - [3ad4a41c4e](https://code.videolan.org/videolan/vlc/-/commit/3ad4a41c4e4c5600f64bd427b27e3ab2a7e4df63) qml: use parent provided selection model in KeyNavigableTableView  
 - [efc179e181](https://code.videolan.org/videolan/vlc/-/commit/efc179e1815b146aed6e3ab590c97e861b0e89c7) qml: load placeholder icons with size VLCStyle.icon_normal for NetworkGridItem  
 - [bbefec5b03](https://code.videolan.org/videolan/vlc/-/commit/bbefec5b037cd7b0d6deb4fabea9d414638e311d) qml: add spacing in between items of NetworkHomeListView  
 - [7322b5f044](https://code.videolan.org/videolan/vlc/-/commit/7322b5f04474c79ad5a6a296038595a3f222621b) qml: change NetworkHomeDisplay's content spacing to margin_small and add topPadding  
 - [8492d78fcd](https://code.videolan.org/videolan/vlc/-/commit/8492d78fcd39d67661086791f198b23b2cf703e9) qml: add left and top padding in headers of NetworkHomeDisplay  
 - [73ddc10364](https://code.videolan.org/videolan/vlc/-/commit/73ddc103643222435da942b0adf1ab2ced87243d) qml: use Subtitle label for headers in NetworkHomeDisplay  
 - [1b35e6e6cc](https://code.videolan.org/videolan/vlc/-/commit/1b35e6e6cc4558e86ac6d516fa2b99ca692e826b) qml: add index property to NetworkGridItem instance in ExpandGridView  
 - [2c1d800afe](https://code.videolan.org/videolan/vlc/-/commit/2c1d800afeb050748f50e82a4f94662138b43a85) qml: change order of tabs in MusicDisplay  
 - [c2c0cc2390](https://code.videolan.org/videolan/vlc/-/commit/c2c0cc2390c6abaf86de6ddc7afbdd03c11339ee) qml: use VLCColors.textDisabled color for disabled history button in top banner  
 - [ba7c50a834](https://code.videolan.org/videolan/vlc/-/commit/ba7c50a8340738c4bc8b298e156d122fcbcd0fc6) qml: use set height for search icon button in SearchBox  
 - [0102a229cb](https://code.videolan.org/videolan/vlc/-/commit/0102a229cbfa4efd7cddbef771ade376a58460e5) qml: add shadow to top Banner  
 - [c344826056](https://code.videolan.org/videolan/vlc/-/commit/c344826056fbf7a01a558b92652b3f544708d564) qml: change background color of localMenuBar  
 - [9dbb4a3088](https://code.videolan.org/videolan/vlc/-/commit/9dbb4a3088ec80a479859a1f766af56e5ebcd244) qml: use VLCIcons.ellipsis as menu icon in BannerSources  
 - [e4018b3339](https://code.videolan.org/videolan/vlc/-/commit/e4018b3339d978420d4199b4c5775d7b5d051f9c) qml: use MenuCaption for texts in SortControl's context menu  
 - [84dbc85789](https://code.videolan.org/videolan/vlc/-/commit/84dbc857895fb0c3f6ca6f822a49f77ca04db8dd) qml: smooth animation in SearchBox  
 - [94c906d245](https://code.videolan.org/videolan/vlc/-/commit/94c906d2456094ab818c7053301e44ab84d7ab77) qml: use VLCStyle's banner_icon_size constant for icon size in BannerSources  
 - [aac2d4eb6f](https://code.videolan.org/videolan/vlc/-/commit/aac2d4eb6ffa04dc959488072851233017b8a8e6) qml: add banner_icon_size constant to VLCStyle  
 - [4f028e687a](https://code.videolan.org/videolan/vlc/-/commit/4f028e687aee19cd00abae93d698b1411213a673) qml: update icon resources used in topbar  
 - [f51161b84a](https://code.videolan.org/videolan/vlc/-/commit/f51161b84a1ec571596ce7268dd16a2adba5d4c4) qml: remove history next button from topbar  
 - [7d1cdd38ac](https://code.videolan.org/videolan/vlc/-/commit/7d1cdd38ac7ca22680f019cf5b65e2f4b40ef11d) qml: rearrange items in BannerSources and resize rows  
 - [8614195fd8](https://code.videolan.org/videolan/vlc/-/commit/8614195fd801ebd4a7885b0f58026c0f64ba0057) qml: add topBarheight and pageBarHeight constants to VLCStyle  
 - [58d5de3d3f](https://code.videolan.org/videolan/vlc/-/commit/58d5de3d3f23b8d7b72edcbc324da0e5852e7401) qml: use BannerTabButton for tabs in BannerSources  
 - [627a46aefe](https://code.videolan.org/videolan/vlc/-/commit/627a46aefebf357975530e10fce935700e38d25b) qml: introduce BannerTabButton widget  
 - [a6246cb426](https://code.videolan.org/videolan/vlc/-/commit/a6246cb42603e67e18f577198aee341e28a39bd4) qml: fix sorting from topbar in MusicGenres  
 - [adf018f674](https://code.videolan.org/videolan/vlc/-/commit/adf018f674856a84edce68ae9d5e64c06e707389) qml: change cover width in list view for genres  
 - [d57038da1d](https://code.videolan.org/videolan/vlc/-/commit/d57038da1d66ea9298c8bf813cae15d6d00dfd1d) qml: use SubtitleLabel for header of Videos Grid view and align headers texts with content  
 - [15de3331e3](https://code.videolan.org/videolan/vlc/-/commit/15de3331e3cf124f847b62da3f64133a75aa9368) qml: fix keyboard action for table view of Music Genres  
 - [3b55343a8f](https://code.videolan.org/videolan/vlc/-/commit/3b55343a8f6fc255f92aa220c276f645a8f5f6bd) qml: use SubtitleLabel for header of Genre albums view and align texts with content  
 - [fa483e92e5](https://code.videolan.org/videolan/vlc/-/commit/fa483e92e58f838e3ef72fedf0cf90ecfbe48668) qml: export rowX property from ExpandGridView  
 - [eba456ab4d](https://code.videolan.org/videolan/vlc/-/commit/eba456ab4d435aef04e734f5fd34cd35a786b096) qml: redesign genres grid items  
 - [d5de61cfa9](https://code.videolan.org/videolan/vlc/-/commit/d5de61cfa945d3bd733277690b8a72730c5c5d40) qt: generate genre covers in 4x2 grid with blur and dark effects  
 - [7a83ea37d2](https://code.videolan.org/videolan/vlc/-/commit/7a83ea37d2930b30d66adecc45d45c656a8623bb) qml: remove 'Genre' text header from Genre view  
 - [a9b877456c](https://code.videolan.org/videolan/vlc/-/commit/a9b877456cd3619f728b0fc1ba8c742175c7e16d) qml: use positioners instead of layout in GridItem  
 - [62758eb7eb](https://code.videolan.org/videolan/vlc/-/commit/62758eb7eb207706748cfd7c18ac3ee9717976da) qml: change background of artist list of MusicArtists  
 - [479b188c1e](https://code.videolan.org/videolan/vlc/-/commit/479b188c1efff8bd866e8cedf1ebac496c6a3caa) qml: add new page to artist view with only artists  
 - [d24fe23fa5](https://code.videolan.org/videolan/vlc/-/commit/d24fe23fa59c1ee43c5ae9dacdf93c10f57de5c7) qml: remove usage of selection model from artistList  
 - [e8b335efc4](https://code.videolan.org/videolan/vlc/-/commit/e8b335efc4968abf86bbab84b55bb67d4f44bae5) qml: center content in GridItems  
 - [9f2491e585](https://code.videolan.org/videolan/vlc/-/commit/9f2491e5858f395578b460517202dc0671df4312) qml: allow changing picture radius and play icon size of GridItem  
 - [336a541c0c](https://code.videolan.org/videolan/vlc/-/commit/336a541c0cedf5db190f4d7de7eec28cfd6892c6) qml: introduce radius for artist covers in VLCStyle  
 - [d020e5b449](https://code.videolan.org/videolan/vlc/-/commit/d020e5b4493afe5a7f0b0f0d01e64a64fc959976) qml: change MusicArtist headers to InlineHeader so that headers scrolls with content  
 - [ebd3f340fb](https://code.videolan.org/videolan/vlc/-/commit/ebd3f340fbd24def95fa023f54ae1684ef677bf2) qml: add 'headerPositioning' property to KeyNavigableTableView  
 - [56897e59c6](https://code.videolan.org/videolan/vlc/-/commit/56897e59c62a0f61c044697cf860d15d784b580a) qml: correct spacing and alignment of ListItem  
 - [614ff0f71d](https://code.videolan.org/videolan/vlc/-/commit/614ff0f71d6d860a0186056e4171dcc70b96e9c9) qml: add border to artist list item's cover images  
 - [5eb739cb81](https://code.videolan.org/videolan/vlc/-/commit/5eb739cb81ecba8738c4e65b859afe5a8027e36a) qml: change artist list item's cover sizes to play_cover_small  
 - [ee76dbae2a](https://code.videolan.org/videolan/vlc/-/commit/ee76dbae2a7ea88d15696cc07f4d627c967d61c7) qml: respect loaded cover size in ListItem  
 - [5d1d4a859f](https://code.videolan.org/videolan/vlc/-/commit/5d1d4a859fdd8dc372e72d447de56530d5b4c52e) qml: add 'Artists' text header to artistList in MusicArtistsDisplay  
 - [287e59be21](https://code.videolan.org/videolan/vlc/-/commit/287e59be218f5123b1f0f2fbbd69f397c6a54522) qml: fix back button for artist page  
 - [a732f4bfc9](https://code.videolan.org/videolan/vlc/-/commit/a732f4bfc9331686def6f2d3f0b22a2d250824e0) qml: don't base MusicArtist to MusicAlbums, create it separately  
 - [4d6db26117](https://code.videolan.org/videolan/vlc/-/commit/4d6db2611704e70586e776fb1962eb225824b8d4) qml: add setCurrentItemFocus function to ExpandGridView  
 - [3cd305f5f5](https://code.videolan.org/videolan/vlc/-/commit/3cd305f5f52b4cbed9c921afeac956bfd0d930ca) qml: add property textHorizontalAlignment to GridItem  
 - [a8ba5735a5](https://code.videolan.org/videolan/vlc/-/commit/a8ba5735a53d8c1e6c05b115202fd42f9e4b53c5) qml: allow ScrollingText to manage center aligned text  
 - [145b49a74b](https://code.videolan.org/videolan/vlc/-/commit/145b49a74be0c9c4a53e49ce8d03d4081ab70f82) qml: add leftMargin, rightMargin and rename marginTop and marginBottom to topMargin and bottomMargin respectively in ExpandGridView  
 - [e2e0489247](https://code.videolan.org/videolan/vlc/-/commit/e2e04892472779e5c480923ce4534230c676d519) qml: add leftMargin, rightMargin, topMargin and bottomMargin properties to KeyNavigableListView  
 - [efd1759ddd](https://code.videolan.org/videolan/vlc/-/commit/efd1759ddd3dddfb0c4fdb85d40b6cdd00411678) qml: make 'selectedBorderWidth' property of GridItem public  
 - [c28d9f4379](https://code.videolan.org/videolan/vlc/-/commit/c28d9f43791824038f386d6bf41f03d6080827ef) qml: refactor artist view from MusicArtistDisplay to separate component  
 - [c6bb178383](https://code.videolan.org/videolan/vlc/-/commit/c6bb178383e12d81fb84a03762d908c35e637054) qml: remove unnecessary property aliases and FocusScope from MusicArtistDisplay  
 - [7fcfc5c34f](https://code.videolan.org/videolan/vlc/-/commit/7fcfc5c34f429cf59a9179023186fce1fc108c2d) qml: redesign ArtistTopBanner  
 - [b450601260](https://code.videolan.org/videolan/vlc/-/commit/b4506012600d57611ecd14063314999cc0e89820) qml: add color constant for round play cover borders  
 - [fc6fe05aec](https://code.videolan.org/videolan/vlc/-/commit/fc6fe05aec00e0f3321891becc2d41e1828a2280) qml: add artistBanner_height constant to VLCStyle  
 - [e4b4e7eb7f](https://code.videolan.org/videolan/vlc/-/commit/e4b4e7eb7fe2014e57b525565798ef02f6e1309e) qml: add color property from TabButtonExt  
 - [e66efd4e1b](https://code.videolan.org/videolan/vlc/-/commit/e66efd4e1bc6747e695b52fd26d01182270f9fa0) qt: add nbtracks property to artist model  
 - [9b71095bf8](https://code.videolan.org/videolan/vlc/-/commit/9b71095bf8d260204bdeab6ba3aa0097969547d0) qml: correctly propagate titleMargin property of GridItem  
 - [cd2943d70e](https://code.videolan.org/videolan/vlc/-/commit/cd2943d70e10d07847b90f1ccee2a5a38b8a8f77) qml: have index as a property for items in ExpandGridView rather then separately attaching it through Object.defineProperty  
 - [6d272069eb](https://code.videolan.org/videolan/vlc/-/commit/6d272069eb6a46c3d5559ce3adc898d94ecc8ea4) qml: apply margintop and marginBottom properties when laying out items  
 - [051f711f35](https://code.videolan.org/videolan/vlc/-/commit/051f711f355e1303bf0ca978875a84c12fb2fc58) qml: remove unused functions from VideoInfoExpandPanel  
 - [44613c2019](https://code.videolan.org/videolan/vlc/-/commit/44613c20194a3a1b423e31285e8fa8ee9e051ffd) qml: redesign VideoInfoExpandPanel  
 - [d9a6dc378b](https://code.videolan.org/videolan/vlc/-/commit/d9a6dc378b7e8da3d35b6247c000e789b252e203) qml: add back icon in VLCIcons  
 - [ee50e1f224](https://code.videolan.org/videolan/vlc/-/commit/ee50e1f224e9fac135e4c0928fd24b03c78785b2) qml: expose video and audio description as separate properties in mlvideo  
 - [239c3370fe](https://code.videolan.org/videolan/vlc/-/commit/239c3370fe4dbb6d6e6720adbf11b6496db4a8f0) qml: redesign music expand delegate  
 - [342cff6e51](https://code.videolan.org/videolan/vlc/-/commit/342cff6e5164ff5ae47d627d57988d5d05efc4b1) qml: expose spacing property in NavigableRow  
 - [87d444cc10](https://code.videolan.org/videolan/vlc/-/commit/87d444cc1079e168a1f7ef2e3b28a94d54d7cf6b) qml: add margin_xxlarge value to VLCStyle  
 - [fe49aaf6bd](https://code.videolan.org/videolan/vlc/-/commit/fe49aaf6bdaf8e9f8cc8950913fa30552f3881a7) qml: add cover sizes for Music Expand Delegate in VLCStyle  
 - [76e631aa8d](https://code.videolan.org/videolan/vlc/-/commit/76e631aa8d775a7f3526ebdbf254355342c055b4) qml: use IconLabel and MenuCaption widget in TabButtonExt  
 - [151e100967](https://code.videolan.org/videolan/vlc/-/commit/151e1009671d335f8e95962b93fcce7988211af2) qml: update play icon and add play_outline and enqueue icons to VLCIcons  
 - [f24e451559](https://code.videolan.org/videolan/vlc/-/commit/f24e4515594cc9b770bdb76904abe63df3a6aa53) qml: apply horizontal and vertical spacing to ExpandItems in ExpandGridView  
 - [fde06372a1](https://code.videolan.org/videolan/vlc/-/commit/fde06372a10ee77d75a5fc6273bc17e87da80103) qml: make ExpandGridView.expandIndex public  
 - [905bf44be3](https://code.videolan.org/videolan/vlc/-/commit/905bf44be39558ffed6302edbb1f94327b3df517) qml: fix expand delegate not showing up for video grid view  
 - [9afe08a7b7](https://code.videolan.org/videolan/vlc/-/commit/9afe08a7b7427f79618facd06f1931d745ce4218) qml: allow to only show borders of GridItem's play cover  
 - [8027b04242](https://code.videolan.org/videolan/vlc/-/commit/8027b04242b7b64b3196b9f3443b42446866f824) qml: implement playClicked signals in AudioGridItem and VideoGridItem  
 - [36ac1cc291](https://code.videolan.org/videolan/vlc/-/commit/36ac1cc29179c74fd14e04da671cb0d47c828e8f) qml: fix no cover for thumbnails in VideoListDisplay  
 - [b58fcbda99](https://code.videolan.org/videolan/vlc/-/commit/b58fcbda9994fceb4e380c56cec8de98de1b082b) qml: add new indicator for GridItem  
 - [973dd7ad56](https://code.videolan.org/videolan/vlc/-/commit/973dd7ad565d921f5bf38919642f793fd7a70878) qml: add shadows to GridItems  
 - [e8d00a95b5](https://code.videolan.org/videolan/vlc/-/commit/e8d00a95b5a878458393c3b63e1788487c331760) qml: set ExpandGridView's spacing with column margins  
 - [971359b092](https://code.videolan.org/videolan/vlc/-/commit/971359b0922d0fad7e65916ea94b6d3a99fa53b3) qml: update griditem properties  
 - [33a5e3157a](https://code.videolan.org/videolan/vlc/-/commit/33a5e3157a74743e17a3d0f81d4116ca5f5eddd8) qml: use MediaCover for image in GridItem  
 - [1b2b431d2b](https://code.videolan.org/videolan/vlc/-/commit/1b2b431d2b665cfa71b4da890c6404bfad5781da) qml: allow arbitary text type in ScrollingText widget  
 - [41df7c94b8](https://code.videolan.org/videolan/vlc/-/commit/41df7c94b84fb17957030985ed903299d1cd857c) qml: introduce MenuLabel widget  
 - [07f39b56aa](https://code.videolan.org/videolan/vlc/-/commit/07f39b56aa300237acfa2b718dcff37727467452) qml: introduce MenuCaption widget  
 - [581d45fa39](https://code.videolan.org/videolan/vlc/-/commit/581d45fa3993c6eca02d937b6d5ed19a99826b94) qml: update GridItem's sizes according to grid system based upon designs  
 - [06feb0bfd2](https://code.videolan.org/videolan/vlc/-/commit/06feb0bfd2239f51f35791e8411d163df1c63543) qml: expose cover border width in MediaCover  
 - [feff28a761](https://code.videolan.org/videolan/vlc/-/commit/feff28a761c96eb6b8602328531f05b7032e75b5) qml: remove isVideo, isNew, infoLeft and 'NEW' label from GridItem  
 - [a3b288e09b](https://code.videolan.org/videolan/vlc/-/commit/a3b288e09ba242fcd274dd112fc11f3795727ca5) qml: change music genre view from list based to table based  
 - [00eecfe3e7](https://code.videolan.org/videolan/vlc/-/commit/00eecfe3e7a3647cb6f2d3611c71a2730f9c7614) qml: emit signal itemDoubleClicked for items in KeyNavigableTableView  
 - [7a2272e9d0](https://code.videolan.org/videolan/vlc/-/commit/7a2272e9d0bc2c6b9c09c1bbf739c33c87120a67) qml: use default column delegate in VideoListDisplay  
 - [13ce4ab4d6](https://code.videolan.org/videolan/vlc/-/commit/13ce4ab4d6bcde5d4afae20db9b2e1a796f2174b) qml: introduce MediaCover widget  
 - [f50e3546b0](https://code.videolan.org/videolan/vlc/-/commit/f50e3546b0bf2172befc4d3fb717684a306e6b41) qml: add context menu in MusicTracksDisplay  
 - [14dc45d73a](https://code.videolan.org/videolan/vlc/-/commit/14dc45d73ab7f2d7d2b1b553321cc5fff8ff2b70) qml: change album list from list based to table based  
 - [e1662eada4](https://code.videolan.org/videolan/vlc/-/commit/e1662eada45d55a66c24772ba849e5c5ddefd76a) qt: add property durationShort to album model  
 - [483648bd6c](https://code.videolan.org/videolan/vlc/-/commit/483648bd6c4943b7794ded659c63e51f2541d454) qt: add first_symbol model roles in album model  
 - [55eb9a6cf6](https://code.videolan.org/videolan/vlc/-/commit/55eb9a6cf6ffe910f3d9fe6e892ed20af858bd65) qt: move getFirstSymbol to MlBaseModel  
 - [d7fc6bb880](https://code.videolan.org/videolan/vlc/-/commit/d7fc6bb880041b0790d71f1b240cbf075b098b43) qml: allow views to define Component to show before table headers in KeyNavigableTableView  
 - [7544444b03](https://code.videolan.org/videolan/vlc/-/commit/7544444b037d8676974a8f370b878a0515115dfc) qml: always show context button in last column of KeyNavigableTableView  
 - [f87e7388c3](https://code.videolan.org/videolan/vlc/-/commit/f87e7388c321fdf49449ecc00376d71c582c8c5a) qml: transfer titleHeaderDelegate and titleDelegate to TableColumns  
 - [1b9ecee821](https://code.videolan.org/videolan/vlc/-/commit/1b9ecee821a6eb194cba34021f60a813407a2bf9) qml: leave space for section lables in KeyNavigableTableView  
 - [fc47af42e8](https://code.videolan.org/videolan/vlc/-/commit/fc47af42e89b338d0ee0edddca89e2a49e1efab7) qml: show separators between items in KeyNavigableTableView  
 - [58c0d38cf3](https://code.videolan.org/videolan/vlc/-/commit/58c0d38cf3a3304a220d5d82f2e9c1ae21d18ba2) qml: centre align section of KeyNavigableTableView  
 - [9c8d6d283a](https://code.videolan.org/videolan/vlc/-/commit/9c8d6d283a7ba885728e1d0dae0c27ad937b71c0) qml: add separator color to VLCColors  
 - [fb54e34fef](https://code.videolan.org/videolan/vlc/-/commit/fb54e34fef8eea6dcf06fc72940662eee9fd20a5) qml: add table section width and margin to VLCStyle  
 - [4e72a40324](https://code.videolan.org/videolan/vlc/-/commit/4e72a4032487c395b51514e5884256be97972c20) qml: change header sequence in VideoList  
 - [f7936adf07](https://code.videolan.org/videolan/vlc/-/commit/f7936adf079137d9ddd0feced75a01ff818bd94f) qml: use default colDelegate in MusicTrackListDisplay  
 - [2757af1ce8](https://code.videolan.org/videolan/vlc/-/commit/2757af1ce8f74d28f9294d388a05ddf1aebcc4a2) qml: show icons as header and centre align text for duration column in MusicAlbumExpandView  
 - [8f9766c181](https://code.videolan.org/videolan/vlc/-/commit/8f9766c18166085288eb001b6a7ad6e2b40cd996) qml: show icons as header and centre align text for duration column in VideoList  
 - [8e26efd030](https://code.videolan.org/videolan/vlc/-/commit/8e26efd030fcf9d6755016e2f91ee4a711174eaf) qml: show icons as header and centre align text for duration column in MusicTrackList  
 - [e52c3db038](https://code.videolan.org/videolan/vlc/-/commit/e52c3db0388eefc65c87be07f95f6a9b6a2ba979) qml: provide specialized time header and column delegates for KeyNavigableTableView  
 - [a8dc9e1489](https://code.videolan.org/videolan/vlc/-/commit/a8dc9e1489240b361270e9358d1dead0abd99e5e) qt: provide durationShort in video and album tracks model  
 - [c98b8e8804](https://code.videolan.org/videolan/vlc/-/commit/c98b8e88046bd19ceeb5efa521cab454793b8bca) qml: use constants for Video and Music track list sizes  
 - [0b3ed042ce](https://code.videolan.org/videolan/vlc/-/commit/0b3ed042ced9197f0046a905cddc28877470533c) qml: add sizes for video and music tracklist in VLCStyle  
 - [79e4d6d749](https://code.videolan.org/videolan/vlc/-/commit/79e4d6d7494ab90195472f66cd6e1aa398b298ac) qml: show bgHover color when row has focus in KeyNavigableTableView  
 - [2a67d1fcce](https://code.videolan.org/videolan/vlc/-/commit/2a67d1fccebba94a4a669f4282b5874eb61c232e) qml: change bgHover of VLCColors to match designs  
 - [8fa5fe13fe](https://code.videolan.org/videolan/vlc/-/commit/8fa5fe13fee6f4ce0f6679f2fb2462bb1baf94b6) qml: show play cover on VideoList cover images  
 - [0ea1f97966](https://code.videolan.org/videolan/vlc/-/commit/0ea1f97966cc6944db0363eac123252d4ffd76b2) qml: show play cover on MusicTrackList cover images  
 - [c3b987f8b0](https://code.videolan.org/videolan/vlc/-/commit/c3b987f8b006871ec793d1d1c71d79705e2ba5f3) qml: add table cover border and cover icon size constants to KeyNavigableTableView  
 - [3b8a7527f1](https://code.videolan.org/videolan/vlc/-/commit/3b8a7527f16f6fd1ff3eae3ef4bb7e1a6afb544e) qml: attach containsMouse and currentlyFocused property to delegates in KeyNavigableTableView  
 - [217007a453](https://code.videolan.org/videolan/vlc/-/commit/217007a4536e3d326c1151567b9668157515d0a4) qml: introduce PlayCover widget  
 - [aba9b7d896](https://code.videolan.org/videolan/vlc/-/commit/aba9b7d8969c12ea12f819d97669d39079468eae) qml: show covers for album tracks  
 - [fce4a4d031](https://code.videolan.org/videolan/vlc/-/commit/fce4a4d031cf2ce011af5d9b2495002043a000da) qt: store thumbnails inside mlAlbumTrack  
 - [23173e0cbb](https://code.videolan.org/videolan/vlc/-/commit/23173e0cbb888634facc284c930d6a9b9a27a8f3) qml: add albums_cover and time icon to VLCIcons  
 - [ce8d3e45fa](https://code.videolan.org/videolan/vlc/-/commit/ce8d3e45fa7acc6db0360f91e582910da800b543) qml: allow header and selective column delegation in KeyNavigableTableView  
 - [c2ca32b6c9](https://code.videolan.org/videolan/vlc/-/commit/c2ca32b6c94c4926cda1410d6b7f0b32d280b63b) qml: introduce ListLabel  
 - [062fa6de9e](https://code.videolan.org/videolan/vlc/-/commit/062fa6de9ea65e9ac3f1df176a915ff2ce7af74a) qml: introduce IconLabel  
 - [809080b075](https://code.videolan.org/videolan/vlc/-/commit/809080b075226246698423b973161982cfbed835) qml: introduce CaptionLabel  
 - [36c9a80841](https://code.videolan.org/videolan/vlc/-/commit/36c9a8084132e66e055cc326070711b57e2db042) qml: introduce fixed width column sizes in KeyNavigableTableView  
 - [f091607387](https://code.videolan.org/videolan/vlc/-/commit/f0916073872ce94d99a4a74e51783b6895e94c39) qml: add column width and margin to VLCStyle  
 - [6c04b13430](https://code.videolan.org/videolan/vlc/-/commit/6c04b134304d227f1890955fa3cdca371a025186) qml: introduce horizontal and vertical spacing property in ExpandGridView  
 - [6a050b88a4](https://code.videolan.org/videolan/vlc/-/commit/6a050b88a4e6c9e730d84aecd19fd044e1966c08) qml: provide extra padding for scroll bar in PlayListView  
 - [3c1d8d2020](https://code.videolan.org/videolan/vlc/-/commit/3c1d8d202050e348aeaa5aa5f446219f4ffb106a) qml: allow sorting through banner for music tracks  
 - [119a3c812e](https://code.videolan.org/videolan/vlc/-/commit/119a3c812ed4f5d1e01ae0fb0d1cead54e3b8319) qml: Only show sort icon if a sort model is available  
