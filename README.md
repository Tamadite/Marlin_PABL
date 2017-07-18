# Probe Assisted Bed Levelling (PABL) 
Repository to feature Marlin with Probe Assited Bed Levelling functionality. 


## IDEA
To make use of the probe to assist on the level of the bed levelling process

## OBJECTIVE
To avoid having a "floating" Z-axis compensating for bad bed levelling

## APPROACH
By making use of the *BED_LEVELING_3POINT* approach:
1. Printhead moves to first bed corner
2.	Nozzle is moved to Z0 (G1 Z0)
3.	User is requested to set the desired distance between nozzle and bed
4.	Probe measures distance (G30 S-1 featuring Z_PROBE_SPEED_SLOW). Distance is shown on display (LCD) as *Zs* (Z set)
5.	Probe moves to next bed corner and measure Z height to bed (G30 S-1 featuring Z_PROBE_SPEED_SLOW). Distance to bed is shown on display as *Zc* (Z to calibrate).
6.	User is requested to level the bed (screwing) accordingly (if *Zc* < *Zs* then bed is low)
7.	User requests a new Z height measure; back to 5 until user request move to next corner.

## NOTES
1.	The above suggestion assumes the nozzle and the probe are mounted on the printhead.
2.	I am successfully exploiting this method but issuing Gcode commands although without featuring Z_PROBE_SPEED_SLOW.
3.	Targeting a bed-nozzle distance of 0.1mm (using a gap measurement blade) I get an average of 0.107mm with StDev 0.01 (ten samples).
  
## EQUIPMENT
  * Geeetech I3 Pro B (GT2560 with Marlin 1.1.4)
  * BLTouch
