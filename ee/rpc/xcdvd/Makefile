# _____     ___ ____     ___ ____
#  ____|   |    ____|   |        | |____|
# |     ___|   |____ ___|    ____| |    \    PS2DEV Open Source Project.
#-----------------------------------------------------------------------
# Copyright 2001-2004, ps2dev - http://www.ps2dev.org
# Licenced under Academic Free License version 2.0
# Review ps2sdk README & LICENSE files for further details.
#
# $Id$


EE_OBJS_DIR = obj/
EE_LIB_DIR = lib/
EE_SRC_DIR = src/
EE_INC_DIR = include/

EE_LIB = libxcdvd.a

LIBCDVD_OBJS = _libcdvd_internals.o sceCdInit.o sceCdIntToPos.o sceCdPosToInt.o \
    sceCdSearchFile.o sceCdDiskReady.o sceCdSemaInit.o sceCdSemaExit.o \
    sceCdInitCallbackThread.o sceCdCallback.o sceCdGenericCallbackFunction.o
LIBCDVD_OBJS := $(LIBCDVD_OBJS:%=$(EE_OBJS_DIR)%)

NCMD_OBJS = _ncmd_internals.o _sceCdAlignReadBuffer.o sceCdRead.o sceCdReadDVDV.o \
    sceCdReadCDDA.o sceCdGetToc.o sceCdSeek.o sceCdStandby.o sceCdStop.o sceCdPause.o \
    sceCdApplyNCmd.o sceCdReadIOPMem.o sceCdNCmdDiskReady.o sceCdReadChain.o \
    sceCdGetReadPos.o sceCdStStart.o sceCdStRead.o sceCdStStop.o sceCdStSeek.o sceCdStInit.o \
    sceCdStStat.o sceCdStPause.o sceCdStResume.o sceCdStream.o sceCdCddaStream.o sceCdSync.o \
    sceCdCheckNCmd.o sceCdReadKey.o
NCMD_OBJS := $(NCMD_OBJS:%=$(EE_OBJS_DIR)%)

SCMD_OBJS = _scmd_internals.o sceCdReadClock.o sceCdWriteClock.o sceCdGetDiskType.o \
    sceCdGetError.o sceCdTrayReq.o sceCdApplySCmd.o sceCdStatus.o sceCdBreak.o \
    sceCdCancelPowerOff.o sceCdBlueLedCtrl.o sceCdPowerOff.o sceCdMMode.o \
    sceCdChangeThreadPriority.o sceCdCheckSCmd.o \
    sceCdForbidDVDP.o sceCdDecSet.o sceCdOpenConfig.o sceCdCloseConfig.o sceCdReadConfig.o \
    sceCdWriteConfig.o sceCdReadNVM.o sceCdWriteNVM.o sceCdRI.o sceCdWI.o \
    sceCdReadConsoleID.o sceCdWriteConsoleID.o sceCdMV.o \
    sceCdBootCertify.o sceCdRM.o sceCdWM.o \
    sceCdSyncS.o
SCMD_OBJS := $(SCMD_OBJS:%=$(EE_OBJS_DIR)%)

EE_LIB := $(EE_LIB:%=$(EE_LIB_DIR)%)
EE_OBJS := $(EE_OBJS:%=$(EE_OBJS_DIR)%) $(EE_OBJS_DIR)erl-support.c

all: $(EE_OBJS_DIR) $(EE_LIB_DIR) $(EE_LIB)

.c.o :
	$(EE_CC) $(EE_CFLAGS) $(EE_INC) -c $< -o obj/$@

$(LIBCDVD_OBJS): src/libcdvd.c
	$(EE_C_COMPILE) -DF_$(*:$(EE_OBJS_DIR)%=%) $< -c -o $@

$(NCMD_OBJS): src/ncmd.c
	$(EE_C_COMPILE) -DF_$(*:$(EE_OBJS_DIR)%=%) $< -c -o $@

$(SCMD_OBJS): src/scmd.c
	$(EE_C_COMPILE) -DF_$(*:$(EE_OBJS_DIR)%=%) $< -c -o $@

EE_OBJS = $(LIBCDVD_OBJS) $(NCMD_OBJS) $(SCMD_OBJS)

clean:
	rm -f -r $(EE_OBJS_DIR) $(EE_LIB_DIR)

include $(PS2SDKSRC)/Defs.make
include $(PS2SDKSRC)/ee/Rules.make
include $(PS2SDKSRC)/ee/Rules.release
