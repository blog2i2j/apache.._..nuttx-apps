############################################################################
# apps/system/uorb/Makefile
#
# SPDX-License-Identifier: Apache-2.0
#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.  The
# ASF licenses this file to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance with the
# License.  You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
# WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  See the
# License for the specific language governing permissions and limitations
# under the License.
#
############################################################################

include $(APPDIR)/Make.defs

CSRCS    += uORB/uORB.c
CSRCS    += $(wildcard sensor/*.c)

ifneq ($(CONFIG_UORB_LOOP_MAX_EVENTS),)
ifneq ($(CONFIG_UORB_LOOP_MAX_EVENTS),0)
CSRCS    += uORB/loop.c uORB/epoll.c
endif
endif

ifneq ($(CONFIG_UORB_LISTENER),)
MAINSRC  += listener.c
PROGNAME += uorb_listener
endif

ifneq ($(CONFIG_UORB_TESTS),)
CSRCS    += test/utility.c
MAINSRC  += test/unit_test.c
PROGNAME += uorb_unit_test
endif

PRIORITY  = $(CONFIG_UORB_PRIORITY)
STACKSIZE = $(CONFIG_UORB_STACKSIZE)
MODULE    = $(CONFIG_UORB)

include $(APPDIR)/Application.mk
