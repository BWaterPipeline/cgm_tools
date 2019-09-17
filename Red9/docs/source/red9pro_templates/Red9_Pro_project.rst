Pro_Pack : project
=======================

	>>> # main import statement to use
	>>> from Red9.pro_pack import PROJECT_DATA
	
ProPack Project object is bound on boot to pro_pack itself and is used to manage data against a clients or projects own
project file. The project file itself is a simple Json formatted file usually found under the client resource folder here:

/Red9_ClientCore/xxxx/resource/xxx.project

The PROJECT_DATA object generated is used anywhere in the Red9 codebase where a path is required which may be specific to a project, 
or folder mount, allowing us to tailor setups to a clients needs without modifying the underlying codebase at all. The project file 
is JSON formatted and bound to the PROJECT_DATA on load, this means that anything in that .project file will be exposed as an attribute 
directly on the PROJECT_DATA.data object.

	>>> # for example
	>>> from Red9.pro_pack import PROJECT_DATA
	>>> PROJECT_DATA.data.fps
	>>> PROJECT_DATA.data.p4_root
	>>> 
	>>> # theres also a pretty print function 
	>>> PROJECT_DATA.pretty_print()
	
Note that PROJECT also manages any initial P4 bindings and therefore exposes some of the root paths directly on the Project object. 
Because of this many of the base paths we may setup in the .project file maybe pre-fixed with p4_root+

	>>> "pose_projectpath": "p4_root+/Data/Animations_Source/Characters/Human/_projectposes/red9/", 

This denotes that the path, in this case the pose_projectpath, is dynamic to the users current P4 workspace mount, we replace the p4_root in this
case with the actual p4_root found in the users system.

Note that on boot we check if source control is available and setup the systems accordingly, all our P4 management codebase, found in the 
importexport module, relies on the PROJECT_DATA.source_control() call, which in itself is setup at boot. This function must return 'perforce'
if any of the systems are to run under the p4 api natively. This NOT limited to P4 and is done in this manner to allow us to bind other source control
systems to the r9File objects dynamically.


.. automodule:: Red9.pro_pack.core.project

   .. rubric:: Main Classes

   .. autosummary::
   	  
      ProjectBase
      Project




    


   
   
   