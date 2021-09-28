### Instalar librerías
#install.packages("viridis")
#install.packages("viridisLite")
#install.packages("tidyverse")
#install.packages("sf")
#install.packages("rayshader")
#install.packages("magick")
#install.packages("av")
#install.packages("ggplot2")
### Activar librerías


library(viridis)
library(viridisLite)
library(tidyverse)
library(sf)
library(rayshader)
library(magick)
library(av)
library(ggplot2)


shp = st_read(dsn = "E:/Proyectos QGIS/3D R/CDMX.shp")


print(shp)

shp = mutate(shp, Datos = POB)


ggshp = ggplot( data = shp)+
  geom_sf(aes(fill = Datos)) +
  scale_fill_viridis()+
  ggtitle("Poblacion CDMX") +
  theme_bw()


plot_gg(ggshp, multicore = TRUE, width = 5, height = 5, scale = 120, 
        windowsize=c(1280,720),zoom = 0.50, phi = 50, sunangle = 120, theta = 45)

render_snapshot()
