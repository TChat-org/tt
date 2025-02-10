# Changes
## src/config.ts
-export const PRODUCTION_HOSTNAME = 'web.teamgram.net';
+export const PRODUCTION_HOSTNAME = '127.0.0.1';

## src/lib/gramjs/Utils.js
-                ipAddress: web.teamgram.net,
-                port: 443,
+                ipAddress: 127.0.0.1,
+                port: 11443,

## src/lib/gramjs/extensions/HttpStream.ts
     static getURL(ip: string, port: number, testServers: boolean, isPremium: boolean) {
         if (port === 443) {
-            return https://${ip}:${port}/apiw1${testServers ? '_test' : ''}${isPremium ? '_premium' : ''};
+            return http://127.0.0.1:8801/apiw1${testServers ? '_test' : ''}${isPremium ? '_premium' : ''};
         } else {
-            return http://${ip}:${port}/apiw1${testServers ? '_test' : ''}${isPremium ? '_premium' : ''};
+            return http://127.0.0.1:8801/apiw1${testServers ? '_test' : ''}${isPremium ? '_premium' : ''};
         }
     }

         await fetch(this.url, {
             method: 'POST',
             body: Buffer.from([]),
-            mode: 'cors',
+            mode: 'no-cors',
             signal: AbortSignal.timeout(REQUEST_TIMEOUT),
         });

## src/lib/gramjs/extensions/PromisedWebSockets.js
     getWebSocketLink(ip, port, testServers, isPremium) {
         if (port === 443) {
-            return wss://${ip}:${port}/apiws${testServers ? '_test' : ''}${isPremium ? '' : ''};
+            return ws://127.0.0.1:11443/apiws${testServers ? '_test' : ''}${isPremium ? '' : ''};
         } else {
-            return ws://${ip}:${port}/apiws${testServers ? '_test' : ''}${isPremium ? '' : ''};
+            return ws://127.0.0.1:11443/apiws${testServers ? '_test' : ''}${isPremium ? '' : ''};
         }
     }

## webpack.config.ts
const CSP = `
  default-src 'self';
-  connect-src 'self' wss://*.web.teamgram.net blob: http: https: ${APP_ENV === 'development' ? 'wss:' : ''};
+  connect-src 'self' ws://127.0.0.1:11443 blob: http: https: ${APP_ENV === 'development' ? 'apiws:' : ''};

