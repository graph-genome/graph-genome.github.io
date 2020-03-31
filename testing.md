[Project Documents](project.html)

![](img/pantograph.png)

# Basic User Test
This process describes the steps for testing each Pull Request (PR) submitted by a contributor.  In the Schematize Browser, we want to make sure that changes are compatible with each other and don't introduce new bugs.

1. Pull code from contributor's repo.
2. `npm install` (Please note if the PR introduces a new npm package requirement).
3. `npm start` Code should compile and launch browser window.
4. Browser window should show Input widgets at top: filename, start bin, left and right buttons, path name, position, jump button, Use Vertical Compression, Row Height, Column Width.
5. Browser window starts populated with a graphic showing the current data.
6. Light grey blocks for coverage (shouldn't be everywhere). Dark grey connectors in between Components (light grey background boxes).  
7. Links appear as colorful arrows immediately above the Component boxes.
8. Link Color matches Box Color in the Column immediately below either end of the link.
9. Links horizontal runs stack up neatly without overlapping (broken in current screenshot).  
10. Mouse over Link and it changes to black.
11. Click Orphan Link (only one small arrow).  View should jump to corresponding section with the other side of the link and matching color.  
12. Matching link is visually highlighted ([#6](https://github.com/graph-genome/Schematize/issues/6) not implemented yet).
13. Clicking on the newly highlighted link should take you back to precisely where you came from (2-way link travel) with your orphan link centered in the view.
14. Mouseover cells (grey blocks) should show e.g. "Path_name: 2365-27289. Coverage: 0.23, Inversion: 0.0".  Mouseovers should be different for each cell. Mouseover disappears when not over cell.

![](img/Example_screenshot.png)


#### TODO:
* Link mouseovers
* Path position "Jump"









## Documentation Index
* [Complete Software Specification (gdoc)](https://docs.google.com/document/d/1NEYkRS6Ux1w_v0Soe74FeOAMOxGHOzDun00LdjMi-74/edit?usp=sharing)
* [Pantograph Description](pantograph.html)
* [Communication and Development Tools](tools.html)
* [Project Resources](project.html)
* [Our Team](https://docs.google.com/document/d/19SHq1P6aWBLKxJbMytW-qZEabWLtYVhoBU09C0uZlV8/edit?usp=sharing)
* [Hackathon](hackathon.html)
* [Get Involved](getinvolved.html)
* [Testing Procedure](testing.html)

