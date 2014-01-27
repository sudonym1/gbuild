* cd to each target and verify:
  * $(git rev-parse HEAD) == .gitmodules for the path
  * $(git status --porcelain | wc -l) == 0
  * That the build exits in $repo
  * If any of these checks fail, rebuild and mark following stages for
    rebuild. (TODO: dont invalidate whole stages, only what must be
    invalidated)
* cd to target, and run commands in order.  If any of them fail, do not
  continue the build, or push anything to the repo.  Builds from a single
  stage could be done in parallel, based on load average (or something else?)
* deliver contents of gbuild.out/ to $repo
