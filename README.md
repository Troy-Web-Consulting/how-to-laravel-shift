# How To: Laravel Shift
Some tips and tricks to make [Laravel Shifting](https://laravelshift.com/) easier.

## Videos:
[Laravel Shift Videos](https://laravelshift.com/videos)
I recommend watching at least the following videos:   

- [Introducing Shift](https://laravelshift.com/videos/introducing-shift)
- [Reviewing the Shift Pull Request](https://laravelshift.com/videos/shift-like-a-pro)
- [Upgrading Old Laravel Applications](https://laravelshift.com/videos/upgrading-old-laravel-applications)
- [Dealing with Dependencies](https://laravelshift.com/videos/update-incompatible-composer-dependencies)

---
## Process
*Any references to video timestamps refer to "Upgrading Old Laravel Applications"*
1. Create an upgrade branch, ex: ```git checkout -b laravel-upgrade```
2. Check for outdated practices (find out more at 0:30).
3. Check for dependency compatibility:  
    1. [Can I upgrade Laravel yet?](https://laravelshift.com/can-i-upgrade-laravel) tool.
    2. Any incompatible/untracked packages should be checked, usually via the package source (composer.json file).
4. Run shift for target repository against the ```laravel-upgrade``` branch.
5. Pull/checkout the newly created branch.
6. When Shift recommends changes to core files (3:10 in video), you can overrite the file with the default file for that Laravel version, then swap the file back at the end of all shifts. Search [Shifts github account](https://github.com/laravel-shift?tab=repositories&q=laravel&type=&language=&sort=) to view these default files by Laravel version. Reapply customizations at the end.
7. Trim PR comments, leaving emojis to indicate status, or delete irrelavent comments. The error comments are the only comments that MUST be addressed now.
8. Merge shift into the ```laravel-upgrade``` branch.

### Additional Steps for LTS Releases
1. Get `composer update --no-scripts` to run. Remove any dependencies that are no longer used. If you are stuck, check out this [very useful video on dealing with composer dependencies](https://laravelshift.com/videos/update-incompatible-composer-dependencies).
2. Clear config, route, or view cache.
3. Attempt to run `php artisan` to make sure that the application runs. Resolve any issues.
4. Move on to merging the PR.

## When you finish shifting
1. Copy any customizations from your pre-shift code on defaulted files, and paste them back into your code. Refactor with any modifications as necessary.

---
## Additional Notes
- I find it very useful to take notes in a document on PR comments you don't *think* matter, but would like to circle back/test later.
- If a popular package is no longer compatible, it is worth looking for open PRs to see if there was any work done to make the package compatible with newer versions. Check out (9:03) in the video for more information. 

---
*Written by Jeremy Langevin*
