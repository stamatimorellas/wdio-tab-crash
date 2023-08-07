# WebDriverIO Tab Crash Error Repro

I have created this repository to reproduce an error I am having with WebDriverIO. I have set this up with a nearly identical structure to my primary project as well as the same dependencies.

See this discussion: https://github.com/webdriverio/webdriverio/discussions/10886

## Example Logs

For additional context, I will show the logs as I see them on my machine. When running `npm run wdio`, I get the following output:

```sh
npm run wdio

> wdio-tab-crash@1.0.0 wdio
> wdio run test/config/wdio.conf.ts


Execution of 1 workers started at 2023-08-07T19:28:25.723Z

2023-08-07T19:28:25.751Z INFO @wdio/cli:launcher: Run onPrepare hook
2023-08-07T19:28:25.755Z INFO @wdio/cli:launcher: Run onWorkerStart hook
2023-08-07T19:28:25.755Z INFO @wdio/local-runner: Start worker 0-0 with arg: run,test/config/wdio.conf.ts
2023-08-07T19:28:25.760Z DEBUG @wdio/local-runner: Send command run to worker with cid "0-0"
[0-0] 2023-08-07T19:28:27.566Z INFO @wdio/local-runner: Run worker command: run
[0-0] 2023-08-07T19:28:27.700Z DEBUG @wdio/runner: init remote session
[0-0] RUNNING in chrome - file:///test/specs/e2e/e2e.ts
[0-0] 2023-08-07T19:28:27.931Z DEBUG @wdio/runner: init remote session
[0-0] 2023-08-07T19:28:30.478Z WARN webdriver: Request failed with status 500 due to disconnected: Unable to receive message from renderer
[0-0]   (failed to check if window was closed: disconnected: not connected to DevTools)
[0-0]   (Session info: headless chrome=115.0.5790.170)
[0-0] 2023-08-07T19:28:30.848Z WARN webdriver: Request failed with status 500 due to tab crashed
[0-0]   (Session info: headless chrome=115.0.5790.170)
[0-0] 2023-08-07T19:28:31.213Z WARN webdriver: Request failed with status 500 due to tab crashed
[0-0]   (Session info: headless chrome=115.0.5790.170)
[0-0] 2023-08-07T19:28:31.536Z ERROR webdriver: Request failed with status 500 due to tab crashed: tab crashed
[0-0]   (Session info: headless chrome=115.0.5790.170)
[0-0] 2023-08-07T19:28:31.536Z ERROR webdriver: tab crashed: tab crashed
[0-0]   (Session info: headless chrome=115.0.5790.170)
[0-0]     at getErrorFromResponseBody (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/webdriver/build/utils.js:194:12)
[0-0]     at NodeJSRequest._request (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/webdriver/build/request/index.js:164:23)
[0-0]     at processTicksAndRejections (node:internal/process/task_queues:95:5)
[0-0]     at async startWebDriverSession (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/webdriver/build/utils.js:63:20)
[0-0]     at async Function.newSession (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/webdriver/build/index.js:28:45)
[0-0]     at async remote (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/webdriverio/build/index.js:45:22)
[0-0]     at async Runner._startSession (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/@wdio/runner/build/index.js:222:29)
[0-0]     at async Runner._initSession (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/@wdio/runner/build/index.js:188:25)
[0-0]     at async Runner.run (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/@wdio/runner/build/index.js:77:19)
[0-0] 2023-08-07T19:28:31.539Z ERROR @wdio/runner: Error: Failed to create session.
[0-0] tab crashed
[0-0]   (Session info: headless chrome=115.0.5790.170)
[0-0]     at startWebDriverSession (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/webdriver/build/utils.js:68:15)
[0-0]     at processTicksAndRejections (node:internal/process/task_queues:95:5)
[0-0]     at async Function.newSession (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/webdriver/build/index.js:28:45)
[0-0]     at async remote (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/webdriverio/build/index.js:45:22)
[0-0]     at async Runner._startSession (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/@wdio/runner/build/index.js:222:29)
[0-0]     at async Runner._initSession (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/@wdio/runner/build/index.js:188:25)
[0-0]     at async Runner.run (file:///Users/stamati/Developer/wdio-tab-crash/node_modules/@wdio/runner/build/index.js:77:19)
2023-08-07T19:28:31.690Z DEBUG @wdio/local-runner: Runner 0-0 finished with exit code 1
[0-0] FAILED in chrome - file:///test/specs/e2e/e2e.ts
2023-08-07T19:28:31.692Z INFO @wdio/cli:launcher: Run onWorkerEnd hook
2023-08-07T19:28:31.693Z INFO @wdio/cli:launcher: Run onComplete hook

Spec Files:	 0 passed, 1 failed, 1 total (100% completed) in 00:00:05

2023-08-07T19:28:31.695Z INFO @wdio/local-runner: Shutting down spawned worker
2023-08-07T19:28:31.947Z INFO @wdio/local-runner: Waiting for 0 to shut down gracefully
2023-08-07T19:28:31.955Z INFO @wdio/local-runner: shutting down
```
