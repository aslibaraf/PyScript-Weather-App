# Weather App Using PyScript + Python


## Code




```python

<!DOCTYPE html>
<html lang="en">
<head>
    <script defer src="https://pyscript.net/alpha/pyscript.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather app</title>
    <link href="https://fonts.googleapis.com/css2?family=Indie+Flower&display=swap" rel="stylesheet">

  <!--================ Design by foolishdeveloper.com ===================-->
    <style media="screen">
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body{
    background: #d7e9d1;
}

/* --------------------background */
.container-fluid{
 width: 410px;
 margin: 50px auto;
 padding: 10px;

}


.inputs {
    padding: 2rem 0 2rem 0;
    text-align: center;
    justify-content: center;
    background: #d7e9d1;
    border-color: black;

}

.inputs input[type="text"] {
    height: 3.5rem;
    width: 20rem;
    background: #212121;
    font-weight: bold;
    font-size: 1.1rem;
    padding: 10px;
    border: none;
    background-color: transparent;
    border: 2px solid #c2c2c2;
    border-radius: 2px;
    margin-right:4px ;

}
.inputs input[type="submit"] {
    height: 3.2rem;
    width: 6.5rem;
    background: #ADD19E;
    font-weight: bold;
    color: white;
    font-size: 1.2rem;
    margin-top: 20px;
    border: none;
    border-radius: 2px;
}

/* -------------------------------display */
.display {
    text-align: center;
    width: 400px;
    color: #16a864;
}
.wrapper {
    margin: 0 9rem;

    background-color: white;
    height: 45vh;
    margin: 50px auto;
    border-radius: 2px;
}

.wrapper h2{
    padding: 5px 0;
    text-align: center;
    background: #ADD19E;
    color: white;
    font-family: sans-serif;
  }
  .wrapper p{
    margin:20px 50px;
    margin-right: 20px;
text-align: left;
color: #04214c;
    font-size:23px;
  }

  .wrapper h2 span{
    font-size: 26px;
    color: #9beefb;
  }
    .wrapper p span{
    color: #90006e;
    font-size: 25px;
  }

    </style>


</head>
<body>
    <div class="container-fluid">



            <section class="main">


    
            <section class="inputs">
                <input type="text" placeholder="Enter any city..." id="cityinput">
                <input type="submit" value="Submit"  pys-onClick="convert"  id="convert">
            <button placeholder="submit" id="add"></button><br><br>

            <a href="https://www.youtube.com/channel/UCOPs4MNMr2QmiWZj2GWx5gg?sub_confirmation=1">
                <button href="google.com" style="font-size:24px">Subcribe Channel <i class="fa fa-youtube-play" style="font-size:48px;color:red"></i>
            </i></button></a>
            

            </section>

     
            <section class="display">
                <div class="wrapper">
                    <h2 id="cityoutput"></h2>
                    
                    <p id="temp"></p>
                    <p id="wind"></p>
                    <p id="humidity"></p>
                    <p id="description"></p>

                </div>
            </section>
            </section>

    </div>

    <py-script>
        from js import document,alert
        from pyodide.http import pyfetch
        import json
        import asyncio
        import re
        def farh(cel):
            return (float(cel) *(9/5)) + 32
        
        async def data(city):
            response = await pyfetch(url="https://api.openweathermap.org/data/2.5/weather?q="+city+"&appid=198700fd07cfb27eb62679f850c5d048", method="GET")
            output = f'{await response.json()}'
            str1 = output.replace("\'", "\"")
            st= json.loads(str1)
            return st        
            
        async def convert(*ags, **kws):
            
            celsius = document.getElementById('cityinput').value;
            result= await data(celsius)
            pyscript.write("cityoutput",f"Weather of {result['name']},{result['sys']['country']}"  )    
            pyscript.write("wind",f"Wind Speed : {result['wind']['speed']}" )  
            pyscript.write("description",f"Weather: {result['weather'][0]['main']}" )    
            pyscript.write("humidity",f"Humidity :  {result['main']['humidity']}" )    
            pyscript.write('temp', "Temperature {} °C".format(round(result['main']['temp']- 273.15,3)))
  

        </py-script>      
</body>
</html>


```



## Developer
[Himalay Parmar](https://github.com/aslibaraf)
