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

## Data Types

The IPSO (IP for Smart Objects) Alliance Smart Objects Guidelines, which identifies each data type with an "Object ID". However, a conversion would have to be made so that the "Object ID" would fit into a single byte and "Object ID" would be added for some types of measurements that are not complemented in IPSO.

Therefore, it was decided to create a new set of data types to be used in agriculture.

### Environmental - base 0x00

<table style="width: 100%;">
<tbody>
<tr>
<td style="font-size: 15px; padding: 10px;"><b>Type</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Code</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Remarks</b></td>
</tr>
<tr>
<td> AIR TEMPERATURE </td>
<td> 0x01 </td>
<td></td>
</tr>
<tr>
<td> AIR HUMIDITY        </td>
<td> 0x02</td>
<td>0% to 100%</td>
</tr>
<tr>
<td> VAPOUR PRESSURE     </td>
<td> 0x03</td>
<td></td>
</tr>
<tr>
<td> BAROMETRIC PRESSURE </td>
<td>0x04</td>
<td></td>
</tr>
<tr>
<td> WIND SPEED          </td>
<td>0x05</td>
<td></td>
</tr>
<tr>
<td> WIND DIRECTION      </td>
<td>0x06</td>
<td></td>
</tr>
<tr>
<td> WIND GUST           </td>
<td>0x07</td>
<td></td>
</tr>
<tr>
<td> PRECIPITATION       </td>
<td>0x08</td>
<td></td>
</tr>
<tr>
<td> LIGHTNING COUNTER   </td>
<td>0x09</td>
<td></td>
</tr>
<tr>
<td> LIGHTNING DISTANCE  </td>
<td>0x0A</td>
<td></td>
</tr>
<tr>
<td> SOLAR RADIATION     </td>
<td>0x0B</td>
<td></td>
</tr>
<tr>
<td> INFRA-RED OBJECT TEMP      </td>
<td>0x0C</td>
<td></td>
</tr>
<tr>
<td> INFRA-RED BODY TEMP       </td>
<td> 0x0D</td>
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
<td style="font-size: 15px; padding: 10px;"><b>Remarks</b></td>
</tr>
<tr>
<td> 
<td> CO2                 0x20
<td> IAQ                 0x21
</tr>
</tbody>
</table>

### Soil - base 0x40

<table style="width: 100%;">
<tbody>
<tr>
<td style="font-size: 15px; padding: 10px;"><b>Type</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Code</b></td>
<td style="font-size: 15px; padding: 10px;"><b>Remarks</b></td>
</tr>
<tr>
<td> SOIL VWC TEROS RAW </td>
<td> 0x40 </td>
<td> Raw Volumetric Water Content - TEROS sensor</td>
</tr>
<tr>
<td> SOIL WATER TENSION </td>
<td> 0x41 </td>
<td> TEROS 21 -> -5kPa to -100000kPa (0.1 kPa) </td>
</tr>
<tr>
<td> SOIL EC </td>
<td> 0x42 </td>
<td>Soil Electrical Conductivity</td>
</tr>
<tr>
<td> SOIL TEMPERATURE 1 </td>
<td> 0x43 </td>
<td> Soil Temperature at depth #1</td>
</tr>
<tr>
<td> SOIL TEMPERATURE 2 </td>
<td> 0x44 </td>
<td> Soil Temperature at depth #2</td>
</tr>
<tr>
<td> SOIL TEMPERATURE 3 </td>
<td> 0x45 </td>
<td> Soil Temperature at depth #3</td>
</tr>
<tr>
<td> SOIL VWC RAW </td>
<td> 0x46 </td>
<td> Raw Volumetric Water Content - other sensors</td>
</tr>
<tr>
<td> SOIL VWC </td>
<td> 0x47 </td>
<td> Volumetric Water Content</td>
</tr>
<tr>
<td> SOIL DIELECTRIC P </td>
<td> 0x50 </td>
<td> Soil Dielectric Permittivity</td>
</tr>
<tr>
<td> SOIL SALINITY </td>
<td> 0x51 </td>
<td></td>
</tr>
<tr>
<td> SOIL TDS </td>
<td> 0x52 </td>
<td> Soil Total Dissolved Solids (TDS)</td>
</tr>
<tr>
<td> SOIL EPSILON </td>
<td> 0x53 </td>
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
<td style="font-size: 15px; padding: 10px;"><b>Remarks</b></td>
</tr>
<tr>
<td> LEAF WETNESS </td>
<td> 0x60 </td>
<td> PHYTOS 31 -> 2.5 to 5 V (300 mV to 1250 mV) </td>
</tr>
<tr>
<td> STEAM WATER POTENTIAL </td>
<td> 0x65 </td>
<td> </td>
</tr>
<tr>
<td> FLORAPULSE READ </td>
<td> 0x66  </td>
<td> output in mV/V of the sensor </td>
</tr>
<tr>
<td> FLORAPULSE RESISTANCE </td>
<td> 0x67 </td>
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