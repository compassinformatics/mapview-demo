# Mapview Demo Project

MapServer Setup for MapView Demo. 

## Datasets

 - Ferry Routes
 	- Linestrings
 - Boreholes
 	- Points
 - Municiple Boundaries
 	- Polygon

## Windows Setup

Install git - https://gitforwindows.org/

```bat
SET PATH=C:\Program Files\Git\bin;%PATH%
git clone "https://github.com/compassinformatics/mapview-demo" "C:\MapServer\apps\mapview-demo"
```

Updates:

```
cd C:\MapServer\apps\mapview-demo & git pull
```

Local URL: http://localhost/mapserver2/?map=D:\GitHub\mapview-demo\cpsi_replace_layers.map&
Live URL: http://w08-mapserver.compass.ie/mapserver/?map=\MapServer\apps\mapview-demo\example.map&

### Troubleshooting

```
msLoadMap(): Unable to access file. (D:\GitHub\mapview-demo\cpsi_replace_layers.map) 
```

Set permissions on folders:

```bat
icacls "C:\MapServer\apps\mapview-demo" /grant IUSR:(OI)(CI)R
icacls "C:\MapServer\apps\mapview-demo" /grant "IIS AppPool\DefaultAppPool":(OI)(CI)R

icacls "C:\MapServer\apps\mapview-demo\log" /grant IUSR:(OI)(CI)RW
icacls "C:\MapServer\apps\mapview-demo\log" /grant "IIS AppPool\DefaultAppPool":(OI)(CI)RW
```

## Linux Setup

TODO

## Command Line Testing

Sample commands for testing WFS responses locally. 

```bat

cd /D D:\GitHub\mapview-demo

mapserv -nh "QUERY_STRING=map=example.map&SERVICE=WFS&VERSION=2.0.0&REQUEST=GetFeature&typeName=ruins&outputFormat=geojson&sortBy=osm_id ASC"

mapserv -nh "QUERY_STRING=map=example.map&SERVICE=WFS&VERSION=2.0.0&REQUEST=GetFeature&typeName=ruins&outputFormat=geojson&sortBy=osm_id ASC"
mapserv -nh "QUERY_STRING=map=example.map&SERVICE=WFS&VERSION=2.0.0&REQUEST=GetFeature&typeName=ruins&outputFormat=geojson&sortBy=osm_id ASC&startIndex=0&count=200"

ogrinfo data/pois.shp
```


