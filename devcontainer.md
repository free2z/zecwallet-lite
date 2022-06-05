## Developing in a container

You can develop zecwallet-lite in a container.`
An example of such a setup can be found here:

<!-- TODO: update with new link once merged -->

https://github.com/free2z/free2z/pull/12/files#diff-13bd9d7a30bf46656bc81f1ad5b908a627f9247be3f7d76df862b0578b534fc6

It is recommended that you run as a non-root user, even in a container.
However, there is a small quirk in chrome-sandbox that it should be owned
by `root`. Because you install with `yarn` as a non-root user,
you are likely to experience this error:

```
[69610:0604/063542.193055:FATAL:setuid_sandbox_host.cc(158)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /workspaces/free2z/zingolabs/zecwallet-lite/node_modules/electron/dist/chrome-sandbox is owned by root and has mode 4755.
```

To fix this error, run the following:

```
sudo chown root:root node_modules/electron/dist/chrome-sandbox
sudo chmod 4755 node_modules/electron/dist/chrome-sandbox
```
