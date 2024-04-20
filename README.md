# hddm_r - i/o library for reading and writing reconstructed events from the GlueX detector

The hddm_r module is a python wrapper around the c++ library that implements reading 
and writing of reconstructed events from the GlueX detector, based on the HDDM event i/o
framework. Every hddm_r file consists of a plain-text header describing the structure
of the event data contained in the file in xml format known as a hddm template. After
the header follows compressed binary data describing the sequence of reconstructed events
contained in the file. All files with valid hddm_r events share a compatible template
indicated by the class="s" attribute in the first line of the file header. All such
files should be readable by this module if they are compliant with the HDDM standard.
For more details on the standard, see https://github.com/rjones30/HDDM.

For details on the hddm_r API, install hddm_r and type "pydoc hddm_r". Here is a 
quickstart example of an analysis tool that reads from hddm_r input files.

import hddm_r
import pyxrootd

for rec in hddm_r.istream("
