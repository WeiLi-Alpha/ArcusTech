TOP=../..

include $(TOP)/configure/CONFIG
#----------------------------------------
#  ADD MACRO DEFINITIONS AFTER THIS LINE
#=============================

#=============================
# Build the IOC application

PROD_IOC = arcus
# arcus.dbd will be created and installed
DBD += arcus.dbd

# arcus.dbd will be made up from these files:
arcus_DBD += base.dbd

# Include dbd files from all support applications:
#arcus_DBD += xxx.dbd
arcus_DBD += calc.dbd
arcus_DBD += stream.dbd
arcus_DBD += asyn.dbd
arcus_DBD += drvAsynSerialPort.dbd

# Add all the support libraries needed by this IOC
#arcus_LIBS += xxx
arcus_LIBS += stream
arcus_LIBS += asyn
arcus_LIBS += calc

# arcus_registerRecordDeviceDriver.cpp derives from arcus.dbd
arcus_SRCS += arcus_registerRecordDeviceDriver.cpp

# Build the main IOC entry point on workstation OSs.
arcus_SRCS_DEFAULT += arcusMain.cpp
arcus_SRCS_vxWorks += -nil-

# Add support from base/src/vxWorks if needed
#arcus_OBJS_vxWorks += $(EPICS_BASE_BIN)/vxComLibrary

# Finally link to the EPICS Base libraries
arcus_LIBS += $(EPICS_BASE_IOC_LIBS)

#===========================

include $(TOP)/configure/RULES
#----------------------------------------
#  ADD RULES AFTER THIS LINE

