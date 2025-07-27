# Local Files for TV Show Trailers and Extras | Plex Support
When using the new **Plex TV Series** agent you can use your own trailers or extras media files. These can be organized in one of two ways to use them with Plex. Either put them “inline”, alongside the tv episode _(in the same season directory as the episode)_, or in a subdirectory of the TV show directory.

**Note:** Certain clients do not yet fully support TV extras but keep an eye out on our forum as our support pages will be updated once official support is available. Currently, the only clients that fully support extras at all levels are the mobile iOS and Android apps. Other apps like the Web client, Android TV, Apple TV and Roku have limited support while the modern TV interface for Smart TVs does not yet have support for any local TV extras.


|Client               |Show|Season|Episode|
|---------------------|:--:|:----:|:-----:|
|Android Mobile, iOS  |✅|✅|✅|
|Plex HTPC, Smart TV’s|✅|✅|✅|
|Roku                 |✅|✅|❌|
|Apple TV, Android TV |✅|❌|✅|
|Plex Web, Desktop    |✅|❌|❌|


Plex Pass Extras
----------------

If you have a Plex Pass subscription you’ll be able to automatically get trailers and extras for shows. Just note that not all Shows have extras available. Just ensure you have the “Find Extras” option enabled in the Advanced section in the TV library’s settings.

**Related:** [Advanced Settings Plex TV Series Agent](https://support.plex.tv/articles/advanced-setting-plex-tv-series-agent/)

Local Show and Season Extras
----------------------------

You can organize your local extras into specific subdirectories inside the main directory named for the TV show. Extras will be detected and used if named and stored as follows:

*   *   *   `TV Show (Release Date)/Extra_Directory_Type/Descriptive_name.ext`

Where `Extra_Directory_Type` is one of:

*   *   *   `Behind The Scenes`
        *   `Deleted Scenes`
        *   `Featurettes`
        *   `Interviews`
        *   `Scenes`
        *   `Shorts`
        *   `Trailers`
        *   `Other`

**Example:**

```
/Game of Thrones
   An Interview With Emilia Clarke-interview.mkv
   /Trailers
      Trailer 1.mkv
      Trailer 2.mkv
   /Featurettes
      Special Effects.mkv
   /Season 01
   /Behind The Scenes
      A look at season 1.mkv
      Season 1 Deleted Scenes-deleted.mkv
```


Local Episode Extras
--------------------

Episode extras can be located alongside the episode file. They’re indicated by using specific naming at the end of the filename. Local inline extras will be detected and used if named and stored as follows:

*   *   *   `S01E01 - Episode Title-Extra_Type.ext`

Where `-Extra_Type` is one of:

*   *   *   \-behindthescenes
        *   \-deleted
        *   \-featurette
        *   \-interview
        *   \-scene
        *   \-short
        *   \-trailer
        *   \-other

**Note**: The filename must end in the `-Extra_Type` value exactly. The hyphen is important and you cannot have spaces after it.

**Examples:**

```
Game of Thrones - S01E01 - Winter is Coming.mkv
Game of Thrones - S01E01 - Winter is Coming-deleted.mkv
Game of Thrones - S01E01 - Winter is Coming-featurette.mkv
```


You can add multiple-episode extras of the same type by adding a number index to the end of the suffix:  
e.g.

```
Game of Thrones - S01E01 - Winter is Coming-deleted1.mkv
Game of Thrones - S01E01 - Winter is Coming-deleted2.mkv
Game of Thrones - S01E01 - Winter is Coming-deleted3.mkv
```


Last modified on: December 5, 2022