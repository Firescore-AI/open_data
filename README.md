# Firescore-AI Open Data

Welcome to the Firescore-AI Open Data repository. This resource is designed to support fire researchers with high-quality, open-access geospatial datasets and AI-enhanced imagery for wildfire risk assessment and mitigation.

We are collaborating with multiple fire departments to field-test advanced hazard-mapping approaches in real-world conditions.

The initial dataset focuses on the City of La Habra Heights, Los Angeles County—a state-recognized high wildfire hazard area.

Key research questions include:

* 	How can remote sensing and AI help identify and monitor fire-prone vegetation in Zone 0?
* What are the operational challenges and opportunities for integrating these data into fire risk management workflows?


## Repository Structure
	• la_habra_heights_ca contains all data
	• sentinel-2 contains ESA sentinel-2 optical data and derivatives 
		• native_res - Contains native resolution band data 
		• super_res - Contains super-resolution data for the same dates
	• usgs_lidar - our cleaned and classified LiDAR from USGS (available nationally)
	
## Working with GeoTIFFs

GeoTIFF images are a special form of imagery which includes special binary tags that help geoposition the image relative to the earth.

These generally require specialized GIS or python tools to display correctly.  If your organization has ESRI ArcMap or similar software, these data should read directly.  The open source qGIS program can also be used.

## Sentinel-2 Optical Imagery

The European Space Agency (ESA) provides open data access to a set of satellites known as Sentinel-2. These provide 13 multispectral bands, ranging in ground sample distance resolution from 10m to 60m. This imagery is available for a given location on earth every 2-5 days. It can be used to generate a number of useful vegetation indices, including NVDI (normalized vegetation difference index), NDRE (normalized difference red edge index) and NDWI (normalized difference wetness index). These are all relevant in assessing vegetation condition, including in the "firesafe" zones around buildings.

Sentinel-2 imagery is ©Copernicus data (2025)

## Image Super-resolution

Zone 0 is define to be 5 feet from structures, or roughly 1.5m, which is not resolvable in raw Sentinel-2 imagery.

Image superresolution is a new AI modeling technique which can be used as the name implies to enhance resolution. How could this possibly work?

The secret turns out to be that very extensive model training is performed, and so the model has learned which combination of higher-resolution pixels are likely and would resolve to a given set of lower-resolution pixels. In the case of the model shown here, this training has been done against approximately 10Tb of high resolution aireal photography (NAIP) and high resolution satellite imagery (from Maxar).

For a discussion of super-resolution techniques in general, please refer to this Nature paper:

[https://www.nature.com/articles/s41597-024-04214-y](https://www.nature.com/articles/s41597-024-04214-y)

The specific super-resolution model used here was S2DR3 from our partner Gamma Earth.  Additional modeling details can be found here:

[https://www.linkedin.com/posts/gamma-earth_sentinel-2-deep-resolution-30-activity-7114515233502580737-DZDA](https://www.linkedin.com/posts/gamma-earth_sentinel-2-deep-resolution-30-activity-7114515233502580737-DZDA?utm_source=share&utm_medium=member_desktop&rcm=ACoAAAF5zjUB_rflNQcZsiALlBm-MaiRm9lFHq4)

## Working with LiDAR Point Clouds
You can either work with the data downloaded locally, or by accessing the point cloud from our server.

Clicking the link below is simplest and should stream data to you via the poTree web application.  Speed will be relative to your location and our US-West server.

[https://lidaru.firescore.ai/firescore_ai/eb/pcd_usgs_lahabracopy.html?c=classification](https://lidaru.firescore.ai/firescore_ai/eb/pcd_usgs_lahabracopy.html?c=classification)

The raw data are also in gitHub, published using their large file storage (lfs).  This should be transparent to you, and you can simply clone all or part of this repo to make a fully local high speed copy.  We recommend the open source "Cloud Compare" software to visualize this type of data, although qGIS and ESRI also work well.

## GIS Files

We have also included some appropriate GIS files for fire hazard planning.

These include terrain and terrain derivatives like slope, aspect and hillshade in a 'terrain' subfolder.

They also include LA County Parcels 2025 and Building Footprints buffered out 5' to Zone 0.

Lastly, we've included a clip of the latest available USGS Landfire data describing the area's fuels.

## Utility and Reliability

As statistician George Box once famously said: "all models are wrong, but some are useful." Our initiative in releasing this imagery and associated datasets is to help researchers or interested hobbiests in assessing the suitability of super-resolution imagery across a variety of digital twin generation or downstream purposes.

We are releasing this under a "Creative Commons Attribution License." Its terms are very generous. Basically we only ask that if you use our work, you give us credit.

Enjoy and let us know what you find!

The FireScore Team

info@firescore.ai

