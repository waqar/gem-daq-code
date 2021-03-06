#
# Makefile for gemHwMonitor package
#
BUILD_HOME:=$(shell pwd)/../..

include $(XDAQ_ROOT)/config/mfAutoconf.rules
include $(XDAQ_ROOT)/config/mfDefs.$(XDAQ_OS)

#Project=gem
Project=gemdaq-testing
Package=gemHwMonitor
LongPackage=gemHwMonitor
ShortPackage=hwMonitor
PackageName=hwMonitor

GEMHWMONITOR_VER_MAJOR=0
GEMHWMONITOR_VER_MINOR=1
GEMHWMONITOR_VER_PATCH=0

Sources =version.cc
Sources+=gemHwMonitorWeb.cc gemHwMonitorBase.cc

DynamicLibrary=gem_hwMonitor

IncludeDirs =$(BUILD_HOME)/$(Project)/$(Package)/include 
IncludeDirs+=$(BUILD_HOME)/$(Project)/gembase/include 
IncludeDirs+=$(BUILD_HOME)/$(Project)/gemutils/include 
IncludeDirs+=$(BUILD_HOME)/$(Project)/gemhardware/include 
IncludeDirs+=$(XDAQ_ROOT)/include 
IncludeDirs+=$(uHALROOT)/include 

DependentLibraryDirs =$(BUILD_HOME)/$(Project)/gembase/lib/$(XDAQ_OS)/$(XDAQ_PLATFORM) 
DependentLibraryDirs+=$(BUILD_HOME)/$(Project)/gemutils/lib/$(XDAQ_OS)/$(XDAQ_PLATFORM) 
DependentLibraryDirs+=$(BUILD_HOME)/$(Project)/gemhardware/lib/$(XDAQ_OS)/$(XDAQ_PLATFORM) 
DependentLibraryDirs+=$(XDAQ_ROOT)/lib 
DependentLibraryDirs+=$(uHALROOT)/lib 

LibraryDirs =
#LibraryDirs+=$(BUILD_HOME)/$(Project)/gembase/lib/$(XDAQ_OS)/$(XDAQ_PLATFORM) 
#LibraryDirs+=$(BUILD_HOME)/$(Project)/gemutils/lib/$(XDAQ_OS)/$(XDAQ_PLATFORM) 
#LibraryDirs+=$(BUILD_HOME)/$(Project)/gemhardware/lib/$(XDAQ_OS)/$(XDAQ_PLATFORM) 
LibraryDirs+=$(XDAQ_ROOT)/lib 
LibraryDirs+=$(uHALROOT)/lib 

PROFILING_Flags =-pg
DEBUG_CFlags  =-O0 -g3 -fno-inline
DEBUG_CCFlags =${DEBUG_CFlags}
UserCFlags  =-std=c++0x ${DEBUG_CFlags}
UserCCFlags =-std=c++0x ${DEBUG_CCFlags}
DEBUG_LDFlags =${PROFILING_Flags}
UserDynamicLinkFlags =
UserStaticLinkFlags =

#UserExecutableLinkFlags =-Wl,-rpath-link ${XDAQ_ROOT}/lib -Wl,-rpath-link $(uHALROOT)/lib -Wl,-rpath-link ${HCAL_XDAQ_ROOT}/lib 
#UserExecutableLinkFlags+=-L$(CACTUS_HOME)/lib 
#UserExecutableLinkFlags+=-lreadline -lncurses -lpthread -lboost_filesystem -lboost_regex -lboost_system -lcactus_extern_pugixml
#UserExecutableLinkFlags+=-lcactus_uhal_log -lcactus_uhal_grammars -lcactus_uhal_uhal

DEBUG_LIBS =profiler tcmalloc
#DependentLibraries =config xcept boost_system cactus_uhal_uhal gem_base
DependentLibraries =config xcept boost_system cactus_uhal_uhal gem_base gem_hw gem_utils
Libraries =config xcept numa toolbox xdaq2rc asyncresolv uuid log4cplus cactus_uhal_uhal

include $(XDAQ_ROOT)/config/Makefile.rules
include $(XDAQ_ROOT)/config/mfRPM.rules
include $(BUILD_HOME)/$(Project)/mfRPM_gem.rules

print-env:
	@echo BUILD_HOME    $(BUILD_HOME)
	@echo XDAQ_ROOT     $(XDAQ_ROOT)
	@echo XDAQ_OS       $(XDAQ_OS)
	@echo XDAQ_PLATFORM $(XDAQ_PLATFORM)
	@echo LIBDIR        $(LIBDIR)
	@echo ROOTCFLAGS    $(ROOTCFLAGS)
	@echo ROOTLIBS      $(ROOTLIBS)
	@echo ROOTGLIBS     $(ROOTGLIBS)
