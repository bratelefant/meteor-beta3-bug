This is just a demo app for reproducing an issue during upgrading from meteor `2.14` to `3.0-beta.0`. On macOS I do

  meteor update --release 3.0-beta.0

and get a minisat error

  MINISAT-out: Cannot enlarge memory arrays. Either (1) compile with -s TOTAL_MEMORY=X with X higher than the current value 67108864, (2) compile with ALLOW_MEMORY_GROWTH which adjusts the size at runtime but prevents some optimizations, or (3) set Module.TOTAL_MEMORY before the program runs. 
  MINISAT-err: Cannot enlarge memory arrays. Either (1) compile with -s TOTAL_MEMORY=X with X higher than the current value 67108864, (2) compile with ALLOW_MEMORY_GROWTH which adjusts the size at runtime but prevents some optimizations, or (3) set Module.TOTAL_MEMORY before the program runs.
  abort() at Error                              
    at jsStackTrace (packages/logic-solver/minisat.js:3:18626)
    at stackTrace (packages/logic-solver/minisat.js:3:18809)
    at abort (packages/logic-solver/minisat.js:33:28956)
    at enlargeMemory (packages/logic-solver/minisat.js:3:19142)
    at Function.dynamicAlloc [as alloc] (packages/logic-solver/minisat.js:3:7927)
    at _sbrk (packages/logic-solver/minisat.js:3:58803)
    at Sd (packages/logic-solver/minisat.js:7:98389)
    at Ud (packages/logic-solver/minisat.js:7:109800)
    at gc (packages/logic-solver/minisat.js:7:41378)
    at pc (packages/logic-solver/minisat.js:7:46259)
    at _b (packages/logic-solver/minisat.js:7:31709)
    at $b (packages/logic-solver/minisat.js:7:35130)
    at Bc (packages/logic-solver/minisat.js:7:54870)
    at hd (packages/logic-solver/minisat.js:7:84479)
    at MiniSat.solveAssuming (packages/logic-solver/minisat_wrapper.js:83:18)
    at Logic.Solver.solve (packages/logic-solver/logic.js:1342:33)
    at Logic.Solver.solveAssuming (packages/logic-solver/logic.js:1375:21)
    at minMaxWS (packages/logic-solver/optimize.js:52:32)
    at packages/constraint-solver/solver.js:429:22
    at CS.Solver.minimize (packages/constraint-solver/solver.js:413:3)
    at CS.Solver.minimize (packages/constraint-solver/solver.js:407:5)
    at CS.Solver._getAnswer (packages/constraint-solver/solver.js:803:3)
    at Object.Logic.disablingAssertions (packages/logic-solver/logic.js:47:12)
    at Function.CS.PackagesResolver._resolveWithInput (packages/constraint-solver/constraint-solver.js:190:10)
    at CS.PackagesResolver.resolve (packages/constraint-solver/constraint-solver.js:151:14)
    at /tools/project-context.js:669:26
    at /tools/project-context.js:665:11
    at Object.enterJob (/tools/utils/buildmessage.js:387:12)
    at /tools/packaging/catalog/catalog.js:100:5
    at Object.capture (/tools/utils/buildmessage.js:282:5)
    at Object.catalog.runAndRetryWithRefreshIfHelpful (/tools/packaging/catalog/catalog.js:99:18)
    at ProjectContext._resolveConstraints (/tools/project-context.js:636:5)
    at /tools/project-context.js:402:9
    at Object.enterJob (/tools/utils/buildmessage.js:387:12)
    at /tools/cli/commands-packages.js:1739:5
    at Object.capture (/tools/utils/buildmessage.js:282:5)
    at Object.main.captureAndExit (/tools/cli/main.js:275:16)
    at maybeUpdateRelease (/tools/cli/commands-packages.js:1738:3)
    at Command.func (/tools/cli/commands-packages.js:1812:29)
    at /tools/cli/main.js:1527:15
  If this abort() is unexpected, build with -s ASSERTIONS=1 which can give more information.

