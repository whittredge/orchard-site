**Styling Bootstrap**

A few attempts were made to create a system to customize the Bootstrap theme, particularly the colors.  I played with three different Sass/SCSS compilers: Koala (macOS app), a Sublime tool (under Tools > Build System > Sass, or Sass Compressed), and pyScss (python lib, for which a new conda env was made in the orchard-site dir from the env file orchard-site.yml).  Also, I installed a CSS Autoprefixer in Sublime (which adds multiple browser prefixes for certain problematic declarations).

Although all of these solutions effectively converted Sass to usable CSS, I struggled to figure out how to modify the Bootstrap root Sass as intended by the developers.  I downloaded the source from the Bootstrap site, but that source seems tailored to their actual site, not Bootstrap in general.  So, I'll revert to the last commit before creating this conda env, then attempt to use NPM to download the source, which I hope will be in a more easily readable and modifiable format than the source I manually downloaded.  (Additionally, I mucked around with a few custom CSS changes that could stand to be reverted for clarity.)  Use: git reset --hard

Ran $ npm install bootstrap@4.0.0-beta.2
This returned some errors---insufficient node version, unmet peer dependencies for jQuery and popper.js---but it also created a node_modules dir, strangely at the same level as orchard-site.

Despite the errors, the node_modules dir contains exactly the useful source I was hoping to work with, in the general file structure described in the Bootstrap documentation.  A new dir called orchard-site_NPM-version was created at the level of orchard-site (in parallel) to experiment with custom CSS.  The dir and site are otherwise the same.

With the new parallel site, I eventually determined how to edit the Bootstrap Scss.  From the custom.scss file, all edits to variables called in Bootstrap must be expressed _before_ Bootstrap is imported with @import.  From here I was able to change the primary and secondary colors, which are currently used in buttons on the site.