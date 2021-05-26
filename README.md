# FetchSSRProblem
Sample project that demonstrates inconsistent Fetch processing behavior for server-side and client-side rendering. Fetch works asynchronously on the client, and synchronously on the server. 


## How to run

1. Clone repo
2. Install NodeJS v.15 or higher
3. Run "npm install" in the cloned repo folder
4. Run "npm run dev" in the cloned repo folder
5. Open http://localhost:3000/ in the browser


## Problems shown

Project has two pages Index and Test. On the Test page where are two components: Foo and Bar. Both components utilizes Fetch to get data (use Promise with setTimeout to emulate real XHR). Foo has 500ms data retriving duration. Bar has 100ms data retriving duration.

1. If we open the Test Page in runtime (client-side render) from the Index page (where is a link Test Page) Fetch inside Foo and Bar components runs asynchronously as can be seen in console:
* Test Page Created
* Foo Created
* Foo Fetch Start
* Bar Created
* Bar Fetch Start
* Bar Fetch End
* Foo Fetch End

2. If we open the TestPage by direct url (server-side render) Fetch inside Foo and Bar components runs synchronously as can be seen in console:
* Test Page Created
* Foo Created
* Foo Fetch Start
* Foo Fetch End
* Bar Created
* Bar Fetch Start
* Bar Fetch End

NuxtJS documentation tells: "Nuxt.js v2.12 introduces a new hook called fetch which you can use **in any of your Vue components**. Use fetch every time you need to get **asynchronous** data."
But in reality all fetch requests are sent one after the other, which leads to huge server side rendering times.
