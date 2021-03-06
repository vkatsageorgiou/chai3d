#  Software License Agreement (BSD License)
#  Copyright (c) 2003-2016, CHAI3D.
#  (www.chai3d.org)
#
#  All rights reserved.
#
#  Redistribution and use in source and binary forms, with or without
#  modification, are permitted provided that the following conditions
#  are met:
#
#  * Redistributions of source code must retain the above copyright
#  notice, this list of conditions and the following disclaimer.
#
#  * Redistributions in binary form must reproduce the above
#  copyright notice, this list of conditions and the following
#  disclaimer in the documentation and/or other materials provided
#  with the distribution.
#
#  * Neither the name of CHAI3D nor the names of its contributors may
#  be used to endorse or promote products derived from this software
#  without specific prior written permission.
#
#  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
#  "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
#  LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS
#  FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE
#  COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,
#  INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
#  BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
#  LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
#  CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
#  LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN
#  ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
#  POSSIBILITY OF SUCH DAMAGE.
#
#  $Author: seb $
#  $Date: 2014-05-01 18:49:45 +1200 (Thu, 01 May 2014) $
#  $Rev: 1316 $


# chai3d location
TOP_DIR = ../..

# chai3d global configuration
include $(TOP_DIR)/Makefile.common

# platform specific flags
ifeq ($(OS), mac)
  QFLAGS = -spec macx-g++ CONFIG-=app_bundle
endif

# configuration specific flags
ifeq ($(CFG),debug)
QFLAGS += CONFIG+=debug
else
QFLAGS += -Wnone
endif

# definitions
NAME   = application-QT
TARGET = $(BIN_DIR)/$(NAME)

# rules
all: $(TARGET)

$(TARGET): Makefile.$(OS).$(ARCH).$(COMPILER) $(EXTERNAL)
	$(MAKE) -f Makefile.$(OS).$(ARCH).$(COMPILER)

Makefile.$(OS).$(ARCH).$(COMPILER):
	qmake $(QFLAGS) QMAKE_CXX=$(CXX) QMAKE_CC=$(CC) QMAKE_LINK=$(CXX) ARCH=$(ARCH) COMPILER=$(COMPILER) CFG=$(CFG) -o Makefile.$(OS).$(ARCH).$(COMPILER)

.PHONY: Makefile.$(OS).$(ARCH).$(COMPILER) $(EXTERNAL)

clean: Makefile.$(OS).$(ARCH).$(COMPILER)
	make -f Makefile.$(OS).$(ARCH).$(COMPILER) clean
	-rm -rf $(TARGET).app $(TARGET) Makefile.$(OS).$(ARCH).$(COMPILER)
