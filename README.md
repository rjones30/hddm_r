# hddm\_r - i/o library for reading and writing reconstructed events from the GlueX detector

The hddm\_r module is a python wrapper around the c++ library that implements reading 
and writing of reconstructed events from the GlueX detector, based on the HDDM event i/o
framework. Every hddm\_r file consists of a plain-text header describing the structure
of the event data contained in the file in xml format known as a hddm template. After
the header follows compressed binary data describing the sequence of reconstructed events
contained in the file. All files with valid hddm\_r events share a compatible template
indicated by the class="s" attribute in the first line of the file header. All such
files should be readable by this module if they are compliant with the HDDM standard.
For more details on the standard, see https://github.com/rjones30/HDDM.

For details on the hddm\_r API, install hddm\_r and type "pydoc hddm\_r". Here is a 
quickstart example of an analysis tool that reads from hddm\_r input files.

	import hddm_r
	for rec in hddm_r.istream("http://nod25.phys.uconn.edu:2880/Gluex/simulation" +
	                          "/simsamples/particle_gun-v5.2.0/particle_gun001_019_rest.hddm"):
	   for pe in rec.getPhysicsEvents():
	      print(f"http streaming reader found run {pe.runNo}, event {pe.eventNo}")
	
	for rec in hddm_r.istream("https://nod25.phys.uconn.edu:2843/Gluex/simulation" +
	                          "/simsamples/particle_gun-v5.2.0/particle_gun001_019_rest.hddm"):
	   for pe in rec.getPhysicsEvents():
	      print(f"https streaming reader found run {pe.runNo}, event {pe.eventNo}")
	
	for rec in hddm_r.istream("root://nod25.phys.uconn.edu/Gluex/simulation" +
	                          "/simsamples/particle_gun-v5.2.0/particle_gun001_019_rest.hddm"):
	   for pe in rec.getPhysicsEvents():
	      print(f"xrootd streaming reader run {pe.runNo}, event {pe.eventNo}")
	
