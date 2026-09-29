---
title: 'Show Manager'
date: '14:07 21-08-2023'
taxonomy:
    category: docs
---

<style>
    #chapter p {
        text-align: left;
    }
table th:first-of-type {
    width: 30%;
}
table th:nth-of-type(2) {
    width: 70%;
}
</style>
### Chapter 5

# Show Manager 

A **Show** is a timeline that arranges other functions (scenes, chasers, audio,
video, …) on **tracks** against time, so a whole performance can be played back
as one. Editing a Show is different from the other functions: it opens its own
full-screen workspace, the **Show Manager**, instead of the right-panel editor.

You enter it by creating a Show from the **Add a new function** menu, or by
double-clicking an existing Show in the Function Manager.

## The timeline

The main area is a **timeline**: time runs left to right, and each horizontal
**track** holds the function items placed on it. A moving **cursor** marks the
current playback position, and a header shows time (or beat) markers.

* **Drag** a function from the right panel's Function Manager onto a track to add
  it to the show at that time.
* **Click** an item to select it; enable multiple selection (right panel) to
  select several.
* **Drag** items along a track to change when they play, or between tracks.
* **Double-click** an item to open the underlying function's own editor.

### Editing while the show plays

A show can be edited while it plays or is paused, and the changes apply
straight away (when paused, as soon as it resumes):

* An item added or moved ahead of the cursor plays when the cursor reaches it.
  One added or moved under the cursor starts straight away, from where the
  cursor is in it, as when the show is played from the middle of the item.
* An item that is playing and gets moved keeps playing without restarting, as
  long as it is still under the cursor, and stops at its new end. Moved past the
  cursor, it stops and plays again when the cursor reaches it.
* Resizing an item that is playing changes when it stops. The show ends at the
  new end of its last item.
* Removing an item, or deleting its function, stops it. A function used by
  another item that is still playing keeps playing for that item.
* Muting a track stops its next items from starting. The items already playing
  go on.
* Tempo sections added, moved, edited or deleted apply to the chasers and EFX
  already playing (see [Tempo sections](#tempo-sections)).

## Toolbar

Across the top:

| Button | What it does |
|--------|--------------|
| **Name** | The show's name. |
| ![](../basics/color.svg?resize=48,48) **Show items color** | Sets the colour of the selected timeline items, to colour-code your show. |
| ![](../basics/lock.svg?resize=48,48) **Lock / Unlock** | Locks the selected items so they can't be moved or resized by accident (the icon toggles between lock and unlock). |
| ![](../basics/grid.svg?resize=48,48) **Snap to grid** | Makes items snap to the time grid when you move them. |
| <i class="fa fa-drum fa-2x"></i> **Show the tempo sections** | Shows the tempo lane below the timeline header (see [Tempo sections](#tempo-sections)). Only available with **Time** markers. |
| <i class="fa fa-arrows-left-right-to-line fa-2x"></i> **Stretch the original function** | When enabled, resizing an item stretches the underlying function's timing to fit, rather than just cropping it. |
| <i class="fa fa-minus fa-2x" style="color:crimson"></i> **Remove the selected items** | Removes the selected items from the show. (The original functions are **not** deleted.) |
| <i class="fa fa-copy fa-2x"></i> **Copy** | Copy the selected items into the clipboard. |
| <i class="fa fa-paste fa-2x"></i> **Paste** | Paste items from the clipboard at the cursor position. |
| **Time display** | The current cursor time. |
| <i class="fa fa-play fa-2x"></i> **Play / Pause** | Play back or pause/resume the Show from the cursor position. |
| <i class="fa fa-stop fa-2x"></i> **Stop / Rewind** | Stop thr Show playback (press again to rewind to the start). |
| **Markers** | The time division shown on the header: **Time**, or beats at **BPM 4/4**, **3/4** or **2/4**. |
| <i class="fa fa-2x fa-magnifying-glass-minus"></i><i class="fa fa-2x fa-magnifying-glass-plus"></i> **Zoom** | Zoom the timeline in and out along the time axis. |

## Tracks

Each track is one row of the timeline.

* Use the <i class="fa fa-plus" style="color:limegreen"></i> **Create a new track** control to add a track.
* When a track is selected, the <i class="fa fa-angle-up"></i> / <i class="fa fa-angle-down"></i> **move track up / down** arrows (top-left of the
  timeline) reorder it among the other tracks.

## Tempo sections

A show often plays several songs one after another, each at its own tempo.
**Tempo sections** tell the Show the tempo of each part of the timeline, so
that chasers set to a **Beats** tempo step exactly on the beat of the song they
play over, instead of following the global BPM.

Click <i class="fa fa-drum"></i> **Show the tempo sections** to show the
**Tempo** lane below the timeline header. It is available when the **Markers**
setting is **Time**. A show that has tempo sections always shows the lane.

Each section has a start, a length, a **BPM** (decimal values such as 127.5 are
allowed), a number of **beats per bar** and a name. The lane shows the bar
numbers and beat ticks of each section, starting from bar 1 at the section
start. Tap a section to select it.

The buttons at the left of the lane:

| Button | What it does |
|--------|--------------|
| <i class="fa fa-plus fa-2x" style="color:limegreen"></i> **Add a tempo section at the cursor** | Adds a section starting at the cursor. It lasts up to the next section, or one minute. |
| <i class="fa fa-music fa-2x"></i> **Add tempo sections from the selected audio items** | Adds a section for each selected audio item, with its position, length and name. When selected items overlap existing sections, it asks how to handle them (see below). |
| <i class="fa fa-pen fa-2x"></i> **Edit the selected tempo section** | Sets the section's **BPM**, **beats per bar** and **name**. Double-clicking a section does the same. |
| <i class="fa fa-scissors fa-2x"></i> **Split the selected tempo section at the cursor** | Splits the section in two at the beat nearest to the cursor, for example where a song changes tempo. Bar numbering starts again at 1 in the second part. |
| <i class="fa fa-trash-can fa-2x" style="color:crimson"></i> **Delete the selected tempo section** | Removes the section. |

A new section opens its editor straight away, since its tempo always needs
setting. **Drag** a section to move it, or drag its left or right edge to resize
it. Sections can't overlap: a section stops at its neighbour, and can sit right
against it. Section edges snap to the edges of the show items.

Songs often overlap at their edges, with the next song starting on a second
audio track before the previous one ends. When some of the selected audio items
overlap existing sections, **Add tempo sections from the selected audio items**
asks whether the new sections should **take over from their start**, which is
ticked by default:

* **Ticked:** the items are taken in start order, and the tempo changes at the
  start of each new song. An existing section is cut where a new one starts. If
  it ran past the end of the new section, it resumes after it, starting on a
  beat of its own grid. A new section ends where an existing one starts, so it
  never cuts into the start of another song. An item where a section already
  starts at the same time is skipped.
* **Not ticked:** only the items that no section overlaps get a section.

To add sections for the second song track, for example, select its items and
click <i class="fa fa-music"></i>.

To line a section up with a song, place its start on the song's first
downbeat, using the audio item waveform as a guide, and set the song's BPM.
Moving a section or changing its tempo never moves the show items. All the
changes to tempo sections can be undone.

### How chasers follow the sections

A chaser set to a **Beats** tempo on a show with tempo sections:

* steps at the tempo of the section it is playing in, and changes steps on that
  section's beats. A chaser placed off the beat changes its first step on the
  nearest beat, then stays on the beat.
* follows the new tempo and beat grid when it runs from one section into the
  next.
* keeps the tempo of the last section in the gap after it, and follows the
  global BPM before the first section.
* lands on the same step when the show is played from the middle of the chaser
  as when it is played from the start.

Its fades, when set by the chaser, are timed at the section tempo too. Chasers
set to a **Time** tempo are not affected.

### How EFX follow the sections

An EFX set to a **Beats** tempo on a show with tempo sections (on a track, in a
collection item, or as a step of a **Beats** tempo chaser):

* counts its beats at the tempo of the section it is playing in, so a loop of 4
  beats takes 4 beats of each song, and its fade in too.
* moves smoothly: when it enters a section, or starts off the beat, its whole
  beats are eased onto that section's beats over one beat, without jumping. An
  item starting exactly half a beat off the beat runs slower for its first
  beat.
* keeps the tempo of the last section in the gap after it, and follows the
  global BPM before the first section.
* is in the same place when the show is played from the middle of the EFX as
  when it is played from the start, and carries on from where it was when the
  show is paused and resumed.
* follows tempo sections edited while it plays, from where it is, eased onto
  the new beats.

A **Beats** tempo EFX started from elsewhere, for example from a Virtual Console
button, while a show with tempo sections plays or is paused within its
sections, follows that show's tempo instead of the global BPM: it takes the
section tempo straight away and locks onto the show's beats within a beat. It
goes back to the global BPM when the show stops, or while the show is before
its first section. An EFX already started from elsewhere keeps doing so when the
show reaches one of its items.

EFX set to a **Time** tempo, and all other functions, are not affected.

Once a show has had tempo sections, it keeps the position of every item in
milliseconds, even if its sections are deleted later. Its **Beats** tempo
chasers then follow the global BPM until the show gets new sections. Switching
the **Markers** to a BPM setting only changes the ruler: the items and the
tempo sections stay as they are.

### Grid and snapping

With **Snap to grid** enabled, the grid inside a section shows its bars and
beats, and adds half and quarter beats when you zoom in. Moving or resizing an
item inside a section snaps it to the finest beat division visible. Snapping to
nearby items still works as usual, and takes priority over the grid, so items
can also be lined up with edges that are off the beat. Outside the sections the
grid and its snapping are unchanged.

### Converting chasers and EFX between Time and Beats tempo

Existing chasers and EFX set to a **Time** tempo can be converted to a **Beats**
tempo at the tempo of a song, and back. Click
<i class="fa fa-right-left fa-2x"></i> **Convert Chasers and EFX between Time and
Beats tempo** in the toolbar, or click the same button next to **Tempo** in the
chaser editor. The converter offers:

* **Convert**: Time tempo chasers and EFX to Beats, or Beats tempo ones to Time.
  For an EFX, its fade in, loop and fade out are converted.
* **Chasers and EFX of**: the selected items, every item of the whole show, or
  every item of all shows, for example a show per act. Chasers and EFX started
  from collections are included, also through nested collections, and take the
  tempo of the section at the start of the collection item. Those already in
  the target tempo are skipped, so you can convert one track at a time.
* **Tempo**: the tempo section under each item (from the chaser editor, the
  section at the cursor), one of the sections, or a BPM you type.
* **Round to**: step times in beats are rounded to the nearest 1, ½, ¼ or ⅛ of
  a beat. Nothing is rounded down to zero.
* **Apply to**: the chasers and EFX themselves, which changes them everywhere
  they are used, or new copies. Copies are used by the selected items, or by every item
  of the show using the original, and the originals stay unchanged. When the
  items are in songs at different tempos, you get one copy per tempo, unless
  you untick **One copy per tempo**. Copies are only made in the show being
  edited.

When a chaser is started from a collection, the collections leading to it are
copied along with it, nested ones included, and the item then starts the copy.
The collections the show used before are left exactly as they are, so their
other uses are unaffected. A collection copy is shared by everything converted
with it: two chasers converted inside one collection give one copy of it rather
than one each, and a collection used in songs at different tempos gets one copy
per tempo, named with the tempo.

The converter shows the converted timings before you apply them, and the other
places a chaser converted in place is used. A chaser converted in place gets a
single tempo, taken from most of its items. The whole conversion can be undone.

Converting a track at a time makes a separate copy of a chaser on each pass, so
the preview says how many more items of the show use a chaser without being
selected. Choose **Whole Show** to convert them all in one pass and get a
single set of copies.

Beats tempo chasers and sequences started by a collection item follow the tempo
sections too.

**Speed Dials:** a Virtual Console Speed Dial sets the times of the functions
it controls in milliseconds, even on a chaser set to a **Beats** tempo, where
they are then read as beats (500 ms becomes half a beat). The converter warns
when a chaser is controlled by a Speed Dial. Disconnect the Speed Dial from
chasers that follow tempo sections, which don't need it.

### Limitations

* Only chasers, sequences and EFX follow the tempo sections so far. Other
  functions set to a **Beats** tempo, such as RGB matrices, still follow the
  global BPM. Only EFX follow the tempo of a show they were not started by.
* In older versions of QLC+, a project with tempo sections still opens, but its
  chasers follow the global BPM, and the items of **Beats** tempo chasers appear
  in the wrong place on the timeline.

## The timing tool

The <i class="fa fa-stopwatch fa-2x" style="color:turquoise"></i> **Timing** button in the right panel opens the **timing tool**, a
panel for adjusting the exact position and length of the items on the timeline
without having to drag them by hand. It is the precise counterpart to
dragging items around: perfect for lining cues up to the frame, or for nudging a
whole selection by a fixed amount.

Everything in the tool follows the show's **Markers** setting: when the timeline
is in **Time** mode, values are shown and entered as time (hours, minutes,
seconds, milliseconds); when it is in one of the **BPM** modes, they are shown
and entered as beats.

The tool is divided into three sections.

### Alignment

Snaps the selected items to the playback **cursor**:

* **Align start to cursor** — moves each selected item so that it *starts* at the
  cursor position.
* **Align end to cursor** — stretches or shrinks each selected item so that it
  *ends* at the cursor position (keeping its start where it is).

### Timings

Shows the **Start time**, **End time** and **Duration** of the selected item.
Click any of the three to reveal a compact **h / m / s / ms** (or beats) editor
in its place, type the exact value, and the item updates immediately:

* With a **single item** selected, the value you type is applied **absolutely** —
  the item is placed exactly there.
* With **several items** selected, the fields read *Multiple* and any change is
  applied **relatively** — the same offset is added to every selected item, so
  you can shift a whole block by, say, +2 seconds at once.

Locked items (see the toolbar's lock button) are left untouched.

### Cut/Insert

Adds or removes a span of time across the **whole show** at the cursor position —
so you can make room for a new section, or close a gap, and everything after the
cursor shifts accordingly:

* **Length** — click to set how much time to cut or insert (in the same h / m / s
  / ms or beats editor).
* **Insert time** — pushes everything after the cursor later by *Length*,
  opening an empty gap.
* **Cut time** — removes a span of *Length* starting at the cursor, pulling
  everything after it earlier.

## Right panel

While in the Show Manager the right panel is the usual
[Function Manager](/function-manager), so you can drag any function onto the
timeline. It also gains the <i class="fa fa-stopwatch fa-2x" style="color:turquoise"></i> **Timing** button described above.
