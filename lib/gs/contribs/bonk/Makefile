#
# %CopyrightBegin%
# 
# Copyright Ericsson AB 1996-2009. All Rights Reserved.
# 
# The contents of this file are subject to the Erlang Public License,
# Version 1.1, (the "License"); you may not use this file except in
# compliance with the License. You should have received a copy of the
# Erlang Public License along with this software. If not, it can be
# retrieved online at http://www.erlang.org/.
# 
# Software distributed under the License is distributed on an "AS IS"
# basis, WITHOUT WARRANTY OF ANY KIND, either express or implied. See
# the License for the specific language governing rights and limitations
# under the License.
# 
# %CopyrightEnd%
#

#
include $(ERL_TOP)/make/target.mk
include $(ERL_TOP)/make/$(TARGET)/otp.mk

# ----------------------------------------------------
# Application version
# ----------------------------------------------------
include ../../vsn.mk
VSN=$(GS_VSN)

# ----------------------------------------------------
# Release directory specification
# ----------------------------------------------------
RELSYSDIR = $(RELEASE_PATH)/lib/gs-$(VSN)/contribs

# ----------------------------------------------------
# Target Specs
# ----------------------------------------------------

MODULES= \
       bonk \
       bonk_sound \
       bonk_square \
       sounder

HRL_FILES= 
ERL_FILES= $(MODULES:%=%.erl)

TARGET_FILES= $(MODULES:%=../ebin/%.$(EMULATOR)) $(TARGET_TOOLBOX_FILES)

BITMAPS= bitmaps/bonkbomb bitmaps/bonkface bitmaps/bonklogo bitmaps/bonkmiss \
	bitmaps/bonktom bitmaps/bonkx bitmaps/erl-e bitmaps/erl-text
SOUNDS= sounds/bonk.au sounds/damn.au sounds/explosion.au sounds/gameover.au \
	sounds/hehee.au sounds/level.au sounds/missedme.au sounds/music.au \
	sounds/ouch!!!.au sounds/praisejesus.au sounds/trumpet.au sounds/yes.au 

TOOLNAME = bonk

EXTRA_FILES= $(TOOLNAME).txt
TOOLBOX_FILES= $(TOOLNAME).tool $(TOOLNAME).gif
TARGET_TOOLBOX_FILES= $(TOOLBOX_FILES:%=$(EBIN)/%)

# ----------------------------------------------------
# FLAGS
# ----------------------------------------------------
ERL_COMPILE_FLAGS +=

# ----------------------------------------------------
# Targets
# ----------------------------------------------------

debug opt: $(TARGET_FILES)

docs:

clean:
	rm -f $(TARGET_FILES)
	rm -f core

# ----------------------------------------------------
# Special Build Targets
# ----------------------------------------------------

$(EBIN)/$(TOOLNAME).gif: $(TOOLNAME).gif
	rm -f $@
	cp $(TOOLNAME).gif $@

$(EBIN)/$(TOOLNAME).tool: $(TOOLNAME).tool
	rm -f $@
	cp $(TOOLNAME).tool $@

# ----------------------------------------------------
# Release Target
# ---------------------------------------------------- 
include $(ERL_TOP)/make/otp_release_targets.mk

release_spec: opt
	$(INSTALL_DIR) $(RELSYSDIR)/ebin
	$(INSTALL_DATA) $(TARGET_FILES) $(RELSYSDIR)/ebin
	$(INSTALL_DIR) $(RELSYSDIR)/bonk/bitmaps
	$(INSTALL_DATA) $(BITMAPS) $(TOOLBOX_FILES) $(RELSYSDIR)/bonk/bitmaps
	$(INSTALL_DIR) $(RELSYSDIR)/bonk/sounds
	$(INSTALL_DATA) $(SOUNDS) $(RELSYSDIR)/bonk/sounds
	$(INSTALL_DIR) $(RELSYSDIR)/bonk
	$(INSTALL_DATA) $(ERL_FILES) $(EXTRA_FILES) $(RELSYSDIR)/bonk


release_docs_spec:

