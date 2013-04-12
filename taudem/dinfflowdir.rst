D-Infinity Flow Directions
==========================

Description
-----------

Assigns a flow direction based on the D-infinity flow method using the steepest
slope of a triangular facet (Tarboton, 1997, "A New Method for the Determination
of Flow Directions and Contributing Areas in Grid Digital Elevation Models",
Water Resources Research, 33(2): 309-319). Flow direction is defined as steepest
downward slope on planar triangular facets on a block centered grid. Flow
direction is encoded as an angle in radians counter-clockwise from east as a
continuous (floating point) quantity between 0 and 2π. The flow direction angle
is determined as the direction of the steepest downward slope on the eight
triangular facets formed in a 3 x 3 grid cell window centered on the grid cell of
interest. The resulting flow in a grid is then usually interpreted as being
proportioned between the two neighboring cells that define the triangular facet
with the steepest downward slope.

.. figure:: images/tardemfig.gif
   :align: center
   :width: 30em

A block-centered representation is used with each elevation value taken to
represent the elevation of the center of the corresponding grid cell. Eight planar
triangular facets are formed between each grid cell and its eight neighbors. Each
of these has a downslope vector which when drawn outwards from the center may be
at an angle that lies within or outside the 45 degree (π/4 radian) angle range
of the facet at the center point. If the slope vector angle is within the facet
angle, it represents the steepest flow direction on that facet. If the slope
vector angle is outside a facet, the steepest flow direction associated with that
facet is taken along the steepest edge. The slope and flow direction associated
with the grid cell is taken as the magnitude and direction of the steepest
downslope vector from all eight facets. Slope is measured as drop/distance,
i.e. tan of the slope angle.

In the case where no slope vectors are positive (downslope), the flow direction
is set using the method of Garbrecht and Martz (1997) for the determination of
flow across flat areas. This makes flat areas drain away from high ground and
towards low ground. The flow path grid to enforce drainage along existing streams
is an optional input, and if used, takes precedence over elevations for the
setting of flow directions.

The D-infinity flow direction algorithm may be applied to a DEM that has not had
its pits filled, but it will then result in "no data" values for the D-infinity
flow direction and slope associated with the lowest point of the pit.

Parameters
----------

- ``Pit Filled Elevation Grid [Raster]``: A grid of elevation values. This is
  usually the output of the **"Pit Remove"** tool, in which case it is elevations
  with pits removed.

Outputs
-------

- ``D-Infinity Flow Direction Grid [Raster]``: A grid of flow directions based
  on the D-infinity flow method using the steepest slope of a triangular facet.
  Flow direction is determined as the direction of the steepest downward slope
  on the 8 triangular facets of a 3 x 3 block centered grid. Flow direction is
  encoded as an angle in radians, counter-clockwise from east as a continuous
  (floating point) quantity between 0 and 2π. The resulting flow in a grid is
  then usually interpreted as being proportioned between the two neighboring
  cells that define the triangular facet with the steepest downward slope.
- ``D-Infinity Slope Grid [Raster]``: A grid of slope evaluated using the
  D-infinity method described in Tarboton, D. G., (1997), "A New Method for the
  Determination of Flow Directions and Contributing Areas in Grid Digital
  Elevation Models", Water Resources Research, 33(2): 309-319. This is the
  steepest outwards slope on one of eight triangular facets centered at each grid
  cell, measured as drop/distance, i.e. tan of the slope angle.

See also
--------


Console usage
-------------
