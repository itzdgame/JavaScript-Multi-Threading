# JavaScript-Multi-Threading
Basic idea of how multi Threading in JavaScript worked using web worker API

File : index.html

<!DOCTYPE HTML>

<html>

   <head>
   
      <title>Multi Threading In Javascript</title>  
     
       <script>

       //   every time use clicked the "Create New Thread" new object will be created parallay 

         function createThread(){

           // new object from Worker class created

           var worker = new Worker('loop.js');

           worker.onmessage = function (event) {

             // data recieved from loop.js

             alert("Completed " + event.data + "iterations" );

           };

         } 

       </script>
   
   </head>
   
   <body>
   
   <input type="button" value="Create New Thread" onclick="createThread()" />
   
   </body>

</html>

File : loop.js

    // simple for loop 

      for (var i = 0; i <= 1000000; i += 1) {

          var x = i;

      }

    // returning the result of loop to parent page

      postMessage(x);
