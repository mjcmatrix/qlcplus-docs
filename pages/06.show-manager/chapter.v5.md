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
| <i class="fa fa-music fa-2x"></i> **Add tempo sections from the selected audio items** | Adds a section for each selected audio item, with its position, length and name. Items that another section overlaps are skipped. |
| <i class="fa fa-pen fa-2x"></i> **Edit the selected tempo section** | Sets the section's **BPM**, **beats per bar** and **name**. Double-clicking a section does the same. |
| <i class="fa fa-scissors fa-2x"></i> **Split the selected tempo section at the cursor** | Splits the section in two at the beat nearest to the cursor, for example where a song changes tempo. Bar numbering starts again at 1 in the second part. |
| <i class="fa fa-trash-can fa-2x" style="color:crimson"></i> **Delete the selected tempo section** | Removes the section. |

A new section opens its editor straight away, since its tempo always needs
setting. **Drag** a section to move it, or drag its left or right edge to resize
it. Sections can't overlap: a section stops at its neighbour, and can sit right
against it. Section edges snap to the edges of the show items.

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
set to a **Time** tempo, and all other functions, are not affected.

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

### Converting chasers between Time and Beats tempo

Existing chasers set to a **Time** tempo can be converted to a **Beats** tempo
at the tempo of a song, and back. Select the chaser items and click
<i class="fa fa-right-left fa-2x"></i> **Convert the selected Chasers between
Time and Beats tempo** in the toolbar, or click the same button next to
**Tempo** in the chaser editor. The converter offers:

* **Convert**: Time tempo chasers to Beats, or Beats tempo chasers to Time.
* **Tempo**: the tempo section under each item (from the chaser editor, the
  section at the cursor), one of the sections, or a BPM you type.
* **Round to**: step times in beats are rounded to the nearest 1, ½, ¼ or ⅛ of
  a beat. Nothing is rounded down to zero.
* **Apply to**: the chasers themselves, which changes them everywhere they are
  used, or new copies. Copies are used by the selected items, or by every item
  of the show using the original, and the originals stay unchanged. When the
  items are in songs at different tempos, you get one copy per tempo, unless
  you untick **One copy per tempo**.

The converter shows the converted timings before you apply them, and the other
places a chaser converted in place is used. The whole conversion can be undone.

**Speed Dials:** a Virtual Console Speed Dial sets the times of the functions
it controls in milliseconds, even on a chaser set to a **Beats** tempo, where
they are then read as beats (500 ms becomes half a beat). The converter warns
when a chaser is controlled by a Speed Dial. Disconnect the Speed Dial from
chasers that follow tempo sections, which don't need it.

### Limitations

* Only chasers and sequences follow the tempo sections so far. Other functions
  set to a **Beats** tempo, such as RGB matrices, still follow the global BPM.
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
