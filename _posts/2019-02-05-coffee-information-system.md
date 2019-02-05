---
layout: post
title: Coffe Information System
---

<div class="message">
<strong>Objective</strong>
Establishment of a coffee information system to provide farmers and stakeholders appropriate on-line tools and data to make better farming, marketing, and business (credit) decisions, marketing up to date information.  The project will include 3 major components: 
</div><br>

> Component 1: Crop growth and production estimates.<br>
> Component 2: Market information.<br>
> Component 3: Business information.<br>

## 1.	Crop growth and production estimates.
The project will use 4-band Landsat 8 <abbr title="Operational Land Imager">OLI</abbr>, High resolution 4-band Multispectral Bundle (QuickBird) Satellite imagery and mobile <abbr title="Geographic Information System">GIS</abbr> app to obtain crop specific information such as:

**1.1 Coffee (area) field boundaries (*old and new coffee plantations*)** <br>
Satellite imagery with a 60-centimeter resolution is obtained from Digital Globe and will be used as the base layer for digitizing.  Digitizing Crop Field Boundaries from the Satellite Imagery will be done in QGIS at a scale of 1:10,000.  The field data are captured and stored in the PostgreSQL database stored in the cloud via QGIS.  These data are uploaded to a local server database.  Comprehensive quality control measures are part of the digitizing process to ensure clean, accurate data of high quality.  The updating schedule and procedures will ensure that the dataset remains current.  A cadastral data management system will be used to build and store parcels, survey points and lines.

**1.2 Diseases and crops infestation**<br>
Diseases and crops infestation monitoring are not only challenging with conducting literally hundreds of surveys annually but also conducting early detection activities for incoming pest and responding hopefully and jointly with other organizations. When a pest is detected we have seen this being addressed with a wide variety of technologies, everything from paper all the way through GIS technology which makes it very challenging to monitor all the information in one place and report on it.  Also, so much time is spent with data collection and transformation that often the overall analysis especially looking at trend suffers.  There are many more workflows and challenges in crop growth and production estimates like BMP (best management practice programs) for nutrient management.  But these are some of the ones that we see and every famers association that we work with and one where GIS is becoming critical to supporting them.  So, using the right information and a timely manner to make better decisions is a crucial step for a successful monitoring.  Whether it’s a response to pest detection, fungal disease, it’s often about streamlining field operations getting away from those paper-based processes and readily connecting to an updating system of record and of course it’s coupled with that increasing overall operational awareness by leveraging authoritative information whether you’re in the field, in the office and throughout entire organization.

Diseases and crops infestation monitoring is a very critical challenge and there are many way GIS can support these efforts.  So overall the processes involve things like setting up monitoring sites, conducting routine or early detection site inspections, tracking the progress of inspection activities, monitoring the results of survey for key or various key performance indicators or conducting and assessment when a critical pest is found.  We developed configurable solutions based on evaluating requirement and in doing this we partnered with ECSI Geo, a local organization with GIS experts.  The solutions we provided are wrapped around various key elements of the workflows, including field survey program monitoring and reporting as well as incident response when pests are detected. the solution implements many of the common patterns: (land use mapping and visualization, data management, field mobility, monitoring, analytics, decision support, sharing & collaboration).

**1.3 Agricultural land use**<br>
We will measure impacts of agricultural land use on stream ecosystems of the coffee-growing. Landform and land use characteristics will be measured for the specific study area. The catchment upstream of each sampling will be delineated from a 1-m resolution Digital Elevation Model (DEM) using the ArcGIS Spatial Analyst tools: fill, flow direction, flow accumulation, stream link, and watershed will be determined.  Streams will be defined using a flow accumulation value of 10,000 to capture small first order drainages. Catchment polygons obtained through this process will be overlaid on 60-cm resolution QuickBird Satellite imagery and brought to field to verify their precision. Land use will be classified using maximum likelihood ratio. Land use polygons for each catchment will be corrected in QGIS using 60-cm resolution QuickBird Satellite imagery and ground-truth information collected in the field. Identified land use included: 
*	bare soil; 
*	cropland;
*	pastures;
*	agroforestry;
*	water;
*	urban land.

Some of these categories will be further divided to investigate possible differential effects of regional land use practices, such as intensive coffee plantations and agroforests species. 

**1.4 Soil moisture conditions**<br>
Soils and soil moisture greatly influence the water cycle and have impacts on runoff, flooding and agriculture. Soil type and soil particle composition (sand, clay, silt) affect soil moisture and the ability of the soil to retain water. Soil moisture is also affected by levels of evaporation and plant transpiration, potentially leading to near dryness and eventual drought.

Measuring and monitoring soil moisture ensure the fitness of coffee crop and help predict or prepare for flash floods and drought 
We will use satellite imagery to monitor soil moisture conditions.  Landsat 4,5,3 are literally used for analysis of soil moisture and vegetation conditions.  Band number 4 reproduces the near infrared, which is useful for determining vegetation types, delineating water bodies, and for soil moisture discrimination. It is often useful to compare band number 4 with band number 5, which represents the mid-infrared.  Band 5 is useful for analyzing vegetation moisture content and soil moisture

The project will make cross analyses of diseases, landuse, moisture variables to make projection on production estimates for targeted agricultural seasons.
 
## 2. Market information 
The project will establish a data collection system to collect marketing information on farm gates prices, export price and middle men prices. This information will be posted online and will be available to farmers, middle men, exporters, and other services providers considering:
*	Extension delivery: web-based platform and mobile app will be created for field extension delivery
*	Market linkages: We will strengthen crops value chain by connecting farmers to commodity buyers
* Information service: market price, weather information, agronomic advice will be available over SMS, voice SMS and call centre.

Storing data always includes the risk that someone will hack into that data. Potentially sensitive market information can play a significant role in marketing information systems, which leads to equally significant risk.  We will use AWS Virtual Private Network (AWS VPN) because it lets us establish a secure and private tunnel from our network or device to the AWS global network. 

## 3.	Business information 
A data base on farmers associations, agricultural input stores and credit institutions working in the targeted areas will be developed.  Data will include: 
* Farmers associations: date of creation, membership, leadership, credit rating, loans obtained, current loans transactions, institutional strength., financial information, credit rating 
* Agricultural input stores:  legal recognition, financial information, list of inputs sold and prices, current loan transactions and credit rating    
* Credit institution:  list of credit institution, type of loans provided, credit requirements, amount of loan provided and interest rate. 

In addition, Crop-speciﬁc maps, created by combining survey data and satellite images, will literally provide the lay of the land for farmers versus agribusinesses such as seed versus fertilizer stores.
Cropland Data Layer inside and outside the farming community will be leveraged in a GIS to perform spatial queries.  It can be extracted and masked out so business entities (farmers associations, credit institution, agricultural input stores) can focus solely on their own interests.

Coffee GIS will be enhanced with Cropland Data Layer.  It has proved helpfulness to farmers associations, credit institutions, agriculture input stores, universities and governments in Information sharing and cross-checking.  A fertilizer store, for example, can use Cropland Data Layer to better anticipate how much fertilizer will be needed in speciﬁc regions. The data is also used by pesticide stores to study pest migration trends and pesticide applications. It is used by farmers and conservationists to perform risk assessment, crop stress. Universities determine research locations based on crop density distribution and develop ecosystem models with CDL (Cropland Data Layer).

A web base application will be developed linking these institutions together to facilitate and activate transactions.  Online banking will also be explored for development.

### Budget summary 
<table>
<tbody>
<tr>
<td>&nbsp;</td>
<td><strong>&nbsp;Price</strong></td>
<td><strong>Unit&nbsp;</strong></td>
<td><strong>Amount&nbsp;</strong></td>
<td><strong>Total&nbsp;</strong></td>
</tr>
<tr>
<td>Project manager</td>
<td>$400</td>
<td>H/j</td>
<td>70</td>
<td>$28,000.00</td>
</tr>
<tr>
<td>Software developer</td>
<td>$200</td>
<td>H/j</td>
<td>70</td>
<td>$14,000.00</td>
</tr>
<tr>
<td>GIS Specialist</td>
<td>$300</td>
<td>H/j</td>
<td>70</td>
<td>$21,000.00</td>
</tr>
<tr>
<td>Mobile platform</td>
<td>$50</td>
<td>month</td>
<td>36</td>
<td>$1,800.00</td>
</tr>
<tr>
<td>AWS instances (Ubuntu server + RDS)</td>
<td>$10</td>
<td>month</td>
<td>36</td>
<td>$360</td>
</tr>
<tr>
<td>Computer(local server)</td>
<td>$1,500</td>
<td>Piece</td>
<td>1</td>
<td>$1,500.00</td>
</tr>
<tr>
<td>Digitizer</td>
<td>$100</td>
<td>H/j</td>
<td>70</td>
<td>$7,000.00</td>
</tr>
<tr>
<td>Technical lead</td>
<td>$200</td>
<td>H/j</td>
<td>70</td>
<td>$14,000.00</td>
</tr>
<tr>
<td>Panchromatic + 4-band Multispectral Bundle (QuickBird) Satellite imagery (60 cm)</td>
<td>$18</td>
<td>sq km</td>
<td>700</td>
<td>$12,250.00</td>
</tr>
</tbody>
</table>

