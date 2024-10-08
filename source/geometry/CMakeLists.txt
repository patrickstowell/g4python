# - build module
#------------------------------------------------------------------------------
set(MODULE pyG4geometry)
#------------------------------------------------------------------------------
pybind11_add_module(${MODULE}
  pyG4BooleanSolid.cc
  pyG4Box.cc
  pyG4ChordFinder.cc
  pyG4Cons.cc
  pyG4Ellipsoid.cc
  pyG4EllipticalCone.cc
  pyG4EllipticalTube.cc
  pyG4Field.cc
  pyG4FieldManager.cc
  pyG4GeometryManager.cc
  pyG4Hype.cc
  pyG4IntersctionSolid.cc
  pyG4LogicalVolume.cc
  pyG4MagneticField.cc
  pyG4Navigator.cc
  pyG4Orb.cc
  pyG4PVPlacement.cc
  pyG4PVReplica.cc
  pyG4Para.cc
  pyG4Polycone.cc
  pyG4Polyhedra.cc
  pyG4Region.cc
  pyG4Sphere.cc
  pyG4SubtractionSolid.cc
  pyG4Tet.cc
  pyG4Torus.cc
  pyG4TouchableHistory.cc
  pyG4TransportationManager.cc
  pyG4Trap.cc
  pyG4Trd.cc
  pyG4Tubs.cc
  pyG4TwistedBox.cc
  pyG4TwistedTrap.cc
  pyG4TwistedTrd.cc
  pyG4TwistedTubs.cc
  pyG4UniformMagField.cc
  pyG4UnionSolid.cc
  pyG4VPhysicalVolume.cc
  pyG4VSolid.cc
  pymodG4geometry.cc
)

target_include_directories(${MODULE} PRIVATE
  ${GEANT4_INCLUDE_DIR}
  ${Python3_INCLUDE_DIRS}
  ${pybind11_INCLUDE_DIR}
)

target_link_directories(${MODULE} PRIVATE ${GEANT4_LIBRARY_DIR})

target_link_libraries(${MODULE} PRIVATE
  ${GEANT4_LIBRARIES} ${Python3_LIBRARIES}
  global_cflags
)

#------------------------------------------------------------------------------
set_target_properties(${MODULE} PROPERTIES PREFIX "")
set_target_properties(${MODULE} PROPERTIES OUTPUT_NAME "G4geometry")
set_target_properties(${MODULE} PROPERTIES SUFFIX ".so")

# install
install(TARGETS ${MODULE} LIBRARY DESTINATION ${G4MODULES_INSTALL_DIR})
