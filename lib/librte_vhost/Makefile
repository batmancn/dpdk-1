# SPDX-License-Identifier: BSD-3-Clause
# Copyright(c) 2010-2014 Intel Corporation

include $(RTE_SDK)/mk/rte.vars.mk

# library name
LIB = librte_vhost.a

EXPORT_MAP := rte_vhost_version.map

LIBABIVER := 4

CFLAGS += -DALLOW_EXPERIMENTAL_API
CFLAGS += $(WERROR_FLAGS) -I$(SRCDIR) -O3 -D_FILE_OFFSET_BITS=64
CFLAGS += -I vhost_user
LDLIBS += -lpthread

ifeq ($(CONFIG_RTE_LIBRTE_VHOST_NUMA),y)
LDLIBS += -lnuma
endif
LDLIBS += -lrte_eal -lrte_mempool -lrte_mbuf -lrte_ethdev -lrte_net \
					-lrte_cryptodev -lrte_hash

# all source are stored in SRCS-y
SRCS-$(CONFIG_RTE_LIBRTE_VHOST) := fd_man.c iotlb.c socket.c vhost.c \
					vhost_user.c virtio_net.c vdpa.c vhost_crypto.c

# install includes
SYMLINK-$(CONFIG_RTE_LIBRTE_VHOST)-include += rte_vhost.h rte_vdpa.h \
					rte_vhost_crypto.h

include $(RTE_SDK)/mk/rte.lib.mk
