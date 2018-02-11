<!doctype html>
<html class="no-js" lang="de">
	<head>
		<meta charset="utf-8" />
		<meta http-equiv="x-ua-compatible" content="ie=edge">
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Foundation Starter Template</title>
		<link rel="stylesheet" href="css/foundation.css" />
	</head>
	<body>


<table class="hover">
  <thead>
    <tr>
      <th width="250">Bereich</th>
      <th>Wert</th>
    </tr>
  </thead>
  <tbody>


	<?php
		$baseURL="http://192.168.2.110:8080";
		$json = file_get_contents($baseURL."/json.htm?type=devices&used=true&filter=all&favorite=1");
		$obj = json_decode($json);
		$array = $obj->result;
//		print_r($json);
		foreach($obj->result as $mydata)
		{
	//     echo $mydata->Type . "<br>";
			$type = $mydata->Type;
			$idx = $mydata->idx;
			$name = $mydata->Name;
			$status = $mydata->Status;
			$SetPoint = $mydata->SetPoint;
			$Temp = $mydata->Temp;
			$Humidity = $mydata->Humidity;
			$arraySwitches = array("Light/Switch", "Group");
			$arrayTemperature = array("Temp + Humidity");
			$arrayThermostat = array("Thermostat");
			
			echo "<tr>";
			echo "<td>".$name."</td>";
			echo "<td>";
			switch (true) {
				case in_array($type, $arraySwitches):
					echo "<form action=\"switch.php?idx=".$idx."\" method='GET'>";		
						switch ($status) {
							case "Off":								
								echo "<div class=\"switch\">";
									echo "<input class=\"switch-input\" id=\"".$idx."\" type=\"checkbox\" onclick=\"this.form.submit();\" name=\"".$idx."\">";
									echo "<label class=\"switch-paddle\" for=\"".$idx."\">";		
										//echo "<span class=\"show-for-sr\">Download Kittens</span>";
							    		echo "<span class=\"switch-active\" aria-hidden=\"true\">On</span>";
							    		echo "<span class=\"switch-inactive\" aria-hidden=\"true\">Off</span>";			
									echo "</label>";
								echo "</div>";
								echo "<input type=\"hidden\" name=\"status\" value=\"On\" />";
								break;
							case "On":
								echo "<div class=\"switch\">";
									echo "<input class=\"switch-input\" id=\"".$idx."\" type=\"checkbox\" onclick=\"this.form.submit();\" name=\"".$idx."\" checked>";
									echo "<label class=\"switch-paddle\" for=\"".$idx."\">";		
										//echo "<span class=\"show-for-sr\">Download Kittens</span>";
							    		echo "<span class=\"switch-active\" aria-hidden=\"true\">On</span>";
							    		echo "<span class=\"switch-inactive\" aria-hidden=\"true\">Off</span>";			
									echo "</label>";
								echo "</div>";
			
								echo "<input type=\"hidden\" name=\"status\" value=\"Off\" />";
								break;
							case "Mixed":
								echo "<div class=\"input-group\">";
								  echo "<span class=\"input-group-label\">Mixed</span>";
									echo "<div class=\"input-group-button\">";										
										echo "<input type=\"submit\" class=\"success button\" name=\"status\" value=\"On\">";
										echo "<input type=\"submit\" class=\"alert button\" name=\"status\" value=\"Off\">";
									echo "</div>";						
								echo "</div>";
								break;
						}				
						echo "<input type=\"hidden\" name=\"idx\" value=\"".$idx."\">";
						echo "<input type=\"hidden\" name=\"type\" value=\"".$type."\">";
					echo "</form>";
					break;
				case in_array($type, $arrayTemperature):
					echo "Temperatur: ".$Temp."° <br>";
					echo "Luftfeuchtigkeit: ".$Humidity."%";
					break;
				case in_array($type, $arrayThermostat):
					echo "Setpoint: ".$SetPoint."°";
					break;					
			}
			echo "</td>";	  
			echo "</tr>";             
		} 	
	?>    
	
  </tbody>
</table>	

	<script src="js/vendor/jquery.js"></script>
	<script src="js/vendor/what-input.js"></script>
	<script src="js/vendor/foundation.min.js"></script>
	<script>
		$(document).foundation();
	</script>

  </body>
</html>