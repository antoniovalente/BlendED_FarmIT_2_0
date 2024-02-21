# Sensor Types for FarmIT 2.0


## Classes of Sensors for Agricultural Application

When used in agriculture, sensors can be divided into three classes: environment, soil and plant. In the class of environmental sensors we can find sensors for air temperature, air humidity, etc. For the soil, we have sensors for soil moisture, soil temperature, among others, while for the class of plant sensors we have: sap flow sensors, temperature and leaf humidity, etc.

## Payload Structure

The LoRaWAN (Long Range Wide Area Network) specification defines the maximum payload size that can be transmitted in a single uplink or downlink message. The maximum payload size depends on the data rate and the region in which the LoRaWAN network operates.

For Europe (EU868) the LoRaWAN protocol defines a maximum payload of 51 bytes.
Taking this into consideration, the following structure was formed for the payload for each node (a node can have more than one type of measurement).

<table style="width: 100%;">
<tbody>
<tr>
<td style="font-size: 15px; padding: 10px;"><b>1 Byte</b></td>
<td style="font-size: 15px; padding: 10px;"><b>1 Byte</b></td>
<td style="font-size: 15px; padding: 10px;"><b>1 Byte</b></td>
<td style="font-size: 15px; padding: 10px;"><b>1 Byte</b></td>
<td style="font-size: 15px; padding: 10px;"><b>1 Byte</b></td>
<td style="font-size: 15px; padding: 10px;"><b>1 Byte</b></td>
<td style="font-size: 15px; padding: 10px;"><b> ... </b></td>
</tr>
<tr>
<td>Data1 Type</td>
<td>Data1 MSB</td>
<td>Data1 LSB</td>
<td>Data2 Type</td>
<td>Data2 MSB</td>
<td>Data2 LSB</td>
<td>...</td>
</tr>
</tbody>
</table>

<b>NOTE:</b> For negative values (temperature) the bit 7 of the MSB will be set to one.

## Data Types

The IPSO (IP for Smart Objects) Alliance Smart Objects Guidelines, which identifies each data type with an "Object ID". However, a conversion would have to be made so that the "Object ID" would fit into a single byte and "Object ID" would be added for some types of measurements that are not complemented in IPSO.

Therefore, it was decided to create a new set of data types to be used in agriculture.

### Environmental - base 0x00

<table style="width: 100%;">
<tbody>
<tr>
<td style="font-size: 15px; padding: 10px;"><b>Type</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Code</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Value (int16)</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Sensor</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Remarks</b></td>
</tr>
<tr>
<td> AIR TEMPERATURE </td>
<td> 0x01 </td>
<td> read * 100</td>
<td> <a href="https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/">BME680</a>, <a href="https://www.sensirion.com/products/catalog/SHTC3/">SHTC3</a>, <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td>BME680 and SHTC3 can be found in WisBlock system</td>
</tr>
<tr>
<td> AIR HUMIDITY        </td>
<td> 0x02</td>
<td> read * 100</td>
<td> <a href="https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/">BME680</a>, <a href="https://www.sensirion.com/products/catalog/SHTC3/">SHTC3</a>, <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td>0% to 100%</td>
</tr>
<tr>
<td> VAPOUR PRESSURE     </td>
<td> 0x03</td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td></td>
</tr>
<tr>
<td> BAROMETRIC PRESSURE </td>
<td>0x04</td>
<td> read * 10</td>
<td> <a href="https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/">BME680</a>, <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td></td>
</tr>
<tr>
<td> WIND SPEED          </td>
<td>0x05</td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/atmos-22/">ATMOS 22</a>, <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td></td>
</tr>
<tr>
<td> WIND DIRECTION      </td>
<td>0x06</td>
<td> read * 10</td>
<td> <a href="https://metergroup.com/products/atmos-22/">ATMOS 22</a>, <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td></td>
</tr>
<tr>
<td> WIND GUST           </td>
<td>0x07</td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/atmos-22/">ATMOS 22</a>, <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td></td>
</tr>
<tr>
<td> PRECIPITATION       </td>
<td>0x08</td>
<td> read / 0.017</td>
<td> <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td></td>
</tr>
<tr>
<td> LIGHTNING COUNTER   </td>
<td>0x09</td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td></td>
</tr>
<tr>
<td> LIGHTNING DISTANCE  </td>
<td>0x0A</td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td></td>
</tr>
<tr>
<td> SOLAR RADIATION     </td>
<td>0x0B</td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/atmos-41/">ATMOS 41</a></td>
<td></td>
</tr>
<tr>
<td> INFRA-RED OBJECT TEMP      </td>
<td>0x0C</td>
<td> read * 100</td>
<td> <a href="https://www.apogeeinstruments.com/sil-411-commercial-grade-sdi-12-digital-output-standard-field-of-view-infrared-radiometer-sensor/">SIL-411</a></td>
<td></td>
</tr>
<tr>
<td> INFRA-RED BODY TEMP       </td>
<td> 0x0D</td>
<td> read * 100</td>
<td> <a href="https://www.apogeeinstruments.com/sil-411-commercial-grade-sdi-12-digital-output-standard-field-of-view-infrared-radiometer-sensor/">SIL-411</a></td>
<td></td>
</tr>
</tbody>
</table>


### Environmental GAS - base 0x02

<table style="width: 100%;">
<tbody>
<tr>
<td style="font-size: 15px; padding: 10px;"><b>Type</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Code</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Value (uint16)</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Sensor</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Remarks</b></td>
</tr>
<tr>
<td> CO2 </td>
<td> 0x20 </td>
<td> read * 100</td>
<td> <a href="https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/">BME680</a></td>
<td> Indirect reading</td>
</tr>
<tr>
<td> IAQ </td>
<td> 0x21 </td>
<td> read * 100</td>
<td> <a href="https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors/bme680/">BME680</a></td>
<td> Indoor Air Quality</td>
</tr>
</tbody>
</table>

### Soil - base 0x40

<table style="width: 100%;">
<tbody>
<tr>
<td style="font-size: 15px; padding: 10px;"><b>Type</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Code</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Value (uint16)</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Sensor</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Remarks</b></td>
</tr>
<tr>
<td> SOIL VWC TEROS RAW </td>
<td> 0x40 </td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/teros-12/">TEROS 12</a></td>
<td> Raw Volumetric Water Content - TEROS sensor</td>
</tr>
<tr>
<td> SOIL WATER TENSION </td>
<td> 0x41 </td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/teros-21/">TEROS 21</a></td>
<td> TEROS 21 -> -5kPa to -100000kPa (0.1 kPa) </td>
</tr>
<tr>
<td> SOIL EC </td>
<td> 0x42 </td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/teros-12/">TEROS 12</a>, <a href="https://s.campbellsci.com/documents/ca/product-brochures/5te_br.pdf">5TE</a>, <a href="https://www.digikey.pt/pt/products/detail/seeed-technology-co.,-ltd/314990620/16570933?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax_Product_All%20Products&utm_term=&productid=16570933&utm_content=&utm_id=go_cmp-20187105315_adg-_ad-__dev-c_ext-_prd-16570933_sig-CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE&gad_source=1&gclid=CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE">SEEED SMS</a></td>
<td> Soil Electrical Conductivity</td>
</tr>
<tr>
<td> SOIL TEMPERATURE 1 </td>
<td> 0x43 </td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/teros-12/">TEROS 12</a>, <a href="https://metergroup.com/products/teros-21/">TEROS 21</a>, <a href="https://www.digikey.pt/pt/products/detail/seeed-technology-co.,-ltd/314990620/16570933?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax_Product_All%20Products&utm_term=&productid=16570933&utm_content=&utm_id=go_cmp-20187105315_adg-_ad-__dev-c_ext-_prd-16570933_sig-CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE&gad_source=1&gclid=CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE">SEEED SMS</a></td>
<td> Soil Temperature at depth #1</td>
</tr>
<tr>
<td> SOIL TEMPERATURE 2 </td>
<td> 0x44 </td>
<td> read * 100</td>
<td> </td>
<td> Soil Temperature at depth #2</td>
</tr>
<tr>
<td> SOIL TEMPERATURE 3 </td>
<td> 0x45 </td>
<td> read * 100</td>
<td> </td>
<td> Soil Temperature at depth #3</td>
</tr>
<tr>
<td> SOIL VWC RAW </td>
<td> 0x46 </td>
<td> read * 100</td>
<td> <a href="https://docs.rakwireless.com/Product-Categories/WisBlock/RAK12035/Datasheet/">RAK12035</a>, Generic SMS</td>
<td> Raw Volumetric Water Content - other sensors</td>
</tr>
<tr>
<td> SOIL VWC </td>
<td> 0x47 </td>
<td> read * 100</td>
<td> <a href="https://www.digikey.pt/pt/products/detail/seeed-technology-co.,-ltd/314990620/16570933?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax_Product_All%20Products&utm_term=&productid=16570933&utm_content=&utm_id=go_cmp-20187105315_adg-_ad-__dev-c_ext-_prd-16570933_sig-CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE&gad_source=1&gclid=CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE">SEEED SMS</a></td>
<td> Volumetric Water Content</td>
</tr>
<tr>
<td> SOIL DIELECTRIC P </td>
<td> 0x50 </td>
<td> read * 100</td>
<td> <a href="https://s.campbellsci.com/documents/ca/product-brochures/5te_br.pdf">5TE</a></td>
<td> Soil Dielectric Permittivity</td>
</tr>
<tr>
<td> SOIL SALINITY </td>
<td> 0x51 </td>
<td> read * 100</td>
<td> <a href="https://www.digikey.pt/pt/products/detail/seeed-technology-co.,-ltd/314990620/16570933?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax_Product_All%20Products&utm_term=&productid=16570933&utm_content=&utm_id=go_cmp-20187105315_adg-_ad-__dev-c_ext-_prd-16570933_sig-CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE&gad_source=1&gclid=CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE">SEEED SMS</a></td>
<td></td>
</tr>
<tr>
<td> SOIL TDS </td>
<td> 0x52 </td>
<td> read * 100</td>
<td> <a href="https://www.digikey.pt/pt/products/detail/seeed-technology-co.,-ltd/314990620/16570933?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax_Product_All%20Products&utm_term=&productid=16570933&utm_content=&utm_id=go_cmp-20187105315_adg-_ad-__dev-c_ext-_prd-16570933_sig-CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE&gad_source=1&gclid=CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE">SEEED SMS</a></td>
<td> Soil Total Dissolved Solids (TDS)</td>
</tr>
<tr>
<td> SOIL EPSILON </td>
<td> 0x53 </td>
<td> read * 100</td>
<td> <a href="https://www.digikey.pt/pt/products/detail/seeed-technology-co.,-ltd/314990620/16570933?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax_Product_All%20Products&utm_term=&productid=16570933&utm_content=&utm_id=go_cmp-20187105315_adg-_ad-__dev-c_ext-_prd-16570933_sig-CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE&gad_source=1&gclid=CjwKCAiA29auBhBxEiwAnKcSqj6BeoKupbwP-RZPg070JTDrAJbdjpTrq6t5b-9uiSRsAz9o3Zma6BoCn0wQAvD_BwE">SEEED SMS</a></td>
<td></td>
</tr>
</tbody>
</table>

### Plant - base 0x60

<table style="width: 100%;">
<tbody>
<tr>
<td style="font-size: 15px; padding: 10px;"><b>Type</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Code</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Value (uint16)</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Sensor</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Remarks</b></td>
</tr>
<tr>
<td> LEAF WETNESS </td>
<td> 0x60 </td>
<td> read * 100</td>
<td> <a href="https://metergroup.com/products/phytos-31/">PHYTOS 31</a></td>
<td> PHYTOS 31 -> 2.5 to 5 V (300 mV to 1250 mV) </td>
</tr>
<tr>
<td> STEAM WATER POTENTIAL </td>
<td> 0x65 </td>
<td> read * 100</td>
<td> <a href="https://www.florapulse.com/">FloraPulse</a></td>
<td> </td>
</tr>
<tr>
<td> FLORAPULSE READ </td>
<td> 0x66  </td>
<td> read * 100</td>
<td> <a href="https://www.florapulse.com/">FloraPulse</a></td>
<td> output in mV/V of the sensor </td>
</tr>
<tr>
<td> FLORAPULSE RESISTANCE </td>
<td> 0x67 </td>
<td> read * 100</td>
<td> <a href="https://www.florapulse.com/">FloraPulse</a></td>
<td>resistance of the onboard thermometer in Ohm </td>
</tr>
</tbody>
</table>

### Miscellaneous - base 0xA0

<table style="width: 100%;">
<tbody>
<tr>
<td style="font-size: 15px; padding: 10px;"><b>Type</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Code</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Remarks</b></td>
</tr>
<tr>
<td> BATTERY </td>
<td> 0xA0 </td>
<td> mV </td>
</tr>
</tbody>
</table>

## More Sensors

More sensors that can be used for agriculture with LoRaWAN (RAK Wireless WisBlock system) can be found <a href="https://store.rakwireless.com/collections/wisblock-sensor">here</a>.


## Decoder at TTN

On the TTN server side, data in the format <DataType><MSB><LSB> will have to be decoded to JSON to be subsequently saved in a database (InfluxDB, for example).

As an example for air humidity values we will have
``` js
data.AirHumidity = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
```


``` js
function decodeUplink(input) {
	var data = {};
	var events = {
		1: "setup",
		2: "environmental data",
		3: "soil data",
		4: "plant data"
	};
	var event_idx = 0;
	
 
	// environmental data
	if (input.fPort === 2) {
	  for(var j = 0; j < input.bytes.length; j += 3) {
		var sensorType = input.bytes[j];

		switch(sensorType) {
			// air temperature
			case 0x01:  if(input.bytes[j+1] > 127) 
							data.AirTemperature = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.AirTemperature = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 2;
						break;
			// air humidity
			case 0x02:  data.AirHumidity = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 2;
						break;
			// vapour pressure
			case 0x03:  data.VapourPressure = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 2;
						break;
			// barometric pressure
			case 0x04:  data.BarometricPressure = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 10.0).toFixed(1));
						event_idx = 2;
						break;
			// wind speed
			case 0x05:  data.WindSpeed = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 2;
						break;
			// wind direction
			case 0x06:  data.WindDirection = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 10.0).toFixed(2));
						event_idx = 2;
						break;
			// wind gust
			case 0x07:  data.WindGust = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 2;
						break;
			// precepitation
			case 0x08:  data.Precipitation = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) * 0.017).toFixed(2));
						event_idx = 2;
						break;            
			// lightnimg counter
			case 0x09:  data.LightningCounter = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2])).toFixed(2));
						event_idx = 2;
						break;            
			// lightning distance
			case 0x0A:  data.LightningDistance = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2])).toFixed(2));
						event_idx = 2;
						break;
			// solar radiation
			case 0x0B:  data.SolarRadiation = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2])).toFixed(2));
						event_idx = 2;
						break;            
			// CO2
			case 0x20:  data.CO2 = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) * 10).toFixed(2));
						event_idx = 2;
						break;
			// IAQ (air quality index)                        
			case 0x21:  data.IAQ = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 2;
						break;
						
			// Soil data -> base 0x40			
			// Soil Volumetric Water Content
			case 0x40:  data.TerosRAWVolumetricWaterContent = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 3;
						break;    			
			// Soil Water Tension             
			case 0x41:  if(input.bytes[j+1] > 127)
							data.SoilWaterTension = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.SoilWaterTension = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 3;
						break;                       
			// Soil EC
			case 0x42:  data.SoilEC = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 3;
						break;                        
			// Soil Temperature #1
			case 0x43:  if(input.bytes[j+1] > 127)
							data.SoilTemperature1 = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.SoilTemperature1 = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 3;
						break;
			// Soil Temperature #2
			case 0x44:  if(input.bytes[j+1] > 127)
							data.SoilTemperature2 = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.SoilTemperature2 = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 3;
						break;
			// Soil Temperature #3
			case 0x45:  if(input.bytes[j+1] > 127)
							data.SoilTemperature3 = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.SoilTemperature3 = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 3;
						break;                        
			// Soil Dieletric Permittivity
			case 0x50:  data.DielectricPermittivity = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 3;
						break;   
			// Soil Raw VolumetricWaterContent           
			case 0x46:  if(input.bytes[j+1] > 127)
							data.RAWVolumetricWaterContent = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-1000.0)).toFixed(3));
						else
							data.RAWVolumetricWaterContent = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 1000.0).toFixed(3));
						event_idx = 3;
						break;  
			// Soil Volumetric Water Content
			case 0x47:  data.VolumetricWaterContent = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 3;
						break;     						
			// Soil Salinity            
			case 0x51:  data.Salinity = parseFloat(((input.bytes[j+1] * 256.0) + input.bytes[j+2]).toFixed(0));
						event_idx = 3;
						break;                       
			// Soil TDS - Total Dissolved Solids            
			case 0x52:  data.SoilTDS = parseFloat(((input.bytes[j+1] * 256.0) + input.bytes[j+2]).toFixed(0));
						event_idx = 3;
						break; 
			// Soil TDS - Total Dissolved Solids            
			case 0x53:  if(input.bytes[j+1] > 127)
							data.SoilEpsilon = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.SoilEpsilon = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 3;
						break;                        

			// Plant -> base 0x60
			// Leaf Wetmess
			case 0x60:  data.LeafWetness = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 1000.0).toFixed(3));
						event_idx = 4;
						break;
			// Steam Water Potential
			case 0x65:  if(input.bytes[j+1] > 127) 
							data.SteamWaterPotential = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.SteamWaterPotential = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 4;
						break;
			// FloraPulse reading of the sensor in mV/V,
			case 0x66:  if(input.bytes[j+1] > 127) 
							data.FloraPulseReading = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.FloraPulseReading = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 4;
						break;
			// FloraPulse thermistor
			case 0x67:  if(input.bytes[j+1] > 127) 
							data.FloraPulseThermistor = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.FloraPulseThermistor = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 4;
						break;
					// SIL-411 Object temperature
			case 0x6C:  if(input.bytes[j+1] > 127) 
							data.IRObjectTemperature = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.IRObjectTemperature = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 4;
						break;
								// SIL-411 Object temperature
			case 0x6D:  if(input.bytes[j+1] > 127) 
							data.IRBodyTemperature = parseFloat(((((input.bytes[j+1] & 0x7F) * 256.0) + input.bytes[j+2]) / (-100.0)).toFixed(2));
						else
							data.IRBodyTemperature = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 100.0).toFixed(2));
						event_idx = 4;
						break;
						
			// battery
			case 0xA0:  data.battery = parseFloat((((input.bytes[j+1]*256.0)+input.bytes[j+2])/1000.0).toFixed(3));
						break;
			// altitude
			case 0xB0:  data.altitude = parseFloat((((input.bytes[j+1] * 256.0) + input.bytes[j+2]) / 10.0).toFixed(2));
						break;
		  } // end case
	  } // end for - sensorType 
	 
	} // end if port = 2

  data.event = events[event_idx];
	
  var warnings = [];
  if (data.battery < 3.000) {
    warnings.push("low battery");
  }
  return {
    data: data,
    warnings: warnings
  };
}

```



An JSON exemple of complete uplink data

``` yaml
{
  "f_port": 2,
  "frm_payload": "AQP/Ahf/",
  "decoded_payload": {
    "AirHumidity": 61.43,
    "AirTemperature": 10.23,
    "event": "environmental data"
  },
  "rx_metadata": [
    {
      "gateway_ids": {
        "gateway_id": "test"
      },
      "rssi": 42,
      "channel_rssi": 42,
      "snr": 4.2
    }
  ],
  "settings": {
    "data_rate": {
      "lora": {
        "bandwidth": 125000,
        "spreading_factor": 7
      }
    },
    "frequency": "868000000"
  }
}
```

Only the decoded payload

``` yaml
{
  "AirHumidity": 61.43,
  "AirTemperature": 10.23,
  "event": "environmental data"
}
```
