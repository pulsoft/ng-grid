# TODO

1. `readableColumnNames` need to be overrideable by i18n.
1. Add banners to compiled .css files (grunt-banner?)
1. Add grunt-nuget task to autodeploy builds to nuget
1. Try to reomve `npm install` commands from travis before-script
1. e2e tests failing on travis, unable to connect to SauceLabs, or timing out?
  1. Maybe try BrowserStack?
1. [DONE] Add util methods that will perform the same as jquery's .height() and .width() on elements.
  1. Still need to test this with hidden elements, and add that functionality. We'll probably use that to calculate row height when possible.
1. Need to make the docs pages allow the user to choose the unstable or stable release (or version) in a drop-down (like Angular does).
1. Refactor elementHeight() calls in scrollbar code, shouldn't need to get it on every scroll event.
1. [IDEA] - Plugin playground. Upload your own plugins and have live examples on a marketplace sort of thing.
1. Make mouse wheel scroll N number of rows, not a specific amount of pixels.
1. "Edit in Plunkr / JsFiddle" buttons don't work. They need to use the absolute url to the script file.
  1. Maybe we can just do another conditional on process.env.TRAVIS and add the <%= site %> on as a prefix.
1. [IDEA] add a test that, during a scroll event, spies on number of reads/writes to DOM properties that cause reflow
1. [IDEA] - For grid search, if the grid has focus and the user presses ctrl/cmd+F we can pop up the search box.

# Done!

1. [DONE] Figure out how to run e2e tests on docs (look at angularjs source / protractor?)
1. [DONE] Add --browsers option for testing on saucelabs with specific browser(s)
1. [DONE] Make karmangular run in `watch` mode and in singlerun too.
1. [DONE] Make sure failing saucelabs tests don't cause the build to fail. Only if the normal test run fails
1. [DONE] Add grunt task that will use ngdoc to build test specs from docs into .tmp/e2e/doc.spec.js
   - It will need to run after ngdocs does. Maybe make a `gendocs` task that runs both serially.
1. [DONE] Docs ref for ui-grid.js is pointing to localhost:9999 on travis.
1. [DONE] Sometimes scrollbar snaps back to the top???
  1. I think it's getting mousewheel events when the element doesn't have focus.
  1. To reproduce, use mousewheel to scroll to bottom of grid, then move outside grid and scroll page to top. Use window scrollbar to move back down to show grid, then click on scrollbar. It will snap to the top.
1. [DONE] elementHeight() (AND jQuery.height()) isn't working on the .ui-grid element. It's not accounting for the border when figuring out the canvas drawing space.
  1. [NOTE] - I just had to subtract "1" from the canvas height. Not sure why. After that, any borders of any size on the grid element are accounted for correctly.
   1 [NOTE] - It was because of the top-panel bottom border, which is 1px by default
1. [DONE] Looks like the canvas needs to be the height of all the elements (rowheight * data length) in order for the scroll to work right
1. [DONE] Add 'track by $index' to ng-repeats?
1. [DONE] Add virtual repeat functionality
1. [DONE] Scrollbar should only show up when there's elements to scroll.
  1. i.e. add ng-show based on canvasHeight > gridbody height
1. [DONE] Copy angular-animate, prettify.js and marked.js into the docs/js dir separately from grunt-ngdocs. It's causing them to show up in `<script>` tags in the Examples which isn't what we want  
1. [DONE] Mouse wheel should work in viewport (almost done)
1. [DONE] - [BUG] - Hidden grid doesn't calculate height of header correctly