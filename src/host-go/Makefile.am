COLM        = @COLM@
COLM_LD     = @COLM_LD@
COLM_LIBDEP = @COLM_LIBDEP@
COLM_BINDEP = @COLM_BINDEP@

bin_PROGRAMS = ragel-go

data_DATA = out-go.lm

ragel_go_CPPFLAGS = -I$(top_srcdir)/aapl

dist_ragel_go_SOURCES = main.cc rlhc.c

nodist_ragel_go_SOURCES = \
	rlparse.c rlreduce.cc

ragel_go_LDADD = ../libragel.la ../libfsm.la $(COLM_LD)

BUILT_SOURCES = rlparse.c rlreduce.cc rlhc.c

EXTRA_DIST = rlparse.lm rlhc.lm

rlparse.c: rlparse.lm $(COLM_BINDEP)
	$(COLM) -I.. -c -b rlparseGo -o $@ -m rlreduce.cc $<

rlreduce.cc: rlparse.c

rlhc.c: rlhc.lm
	$(COLM) -I.. -c -b rlhcGo -o $@ $<
