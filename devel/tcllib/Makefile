# Created by: Mikhail Teterin <mi@aldan.algebra.com>
# $FreeBSD$

PORTNAME=	tcllib
PORTVERSION=	1.17
PORTREVISION=	1
CATEGORIES=	devel tcl

MAINTAINER=	tcltk@FreeBSD.org
COMMENT=	Collection of utility modules for Tcl

LICENSE=	TclTk
LICENSE_NAME=	Tcl/Tk License
LICENSE_FILE=	${WRKSRC}/license.terms
LICENSE_PERMS=	dist-mirror dist-sell pkg-mirror pkg-sell auto-accept

BUILD_DEPENDS=	critcl:${PORTSDIR}/devel/critcl

OPTIONS_DEFINE=	DOCS MANPAGES

USE_GITHUB=	yes
GH_ACCOUNT=	tcltk
GH_TAGNAME=	${PORTNAME}_${PORTVERSION:S/./_/}

USES+=		tcl
GNU_CONFIGURE=	yes
CONFIGURE_ENV+=	ac_cv_path_tclsh="${TCLSH}"
ALL_TARGET=	critcl
MAKE_ENV+=	LANG=C
PORTDOCS=	*
REINPLACE_ARGS=	-i'""'
PLIST_SUB+=	BINARCH=${OPSYS:tl}-${ARCH:S/i386/ix86/}

INSTALL_ARGS=	-pkgs -pkg-path ${STAGEDIR}${PREFIX}/lib/tcllib \
		-apps -app-path ${STAGEDIR}${PREFIX}/bin \
		-no-wait -no-gui -no-examples

.include <bsd.port.options.mk>

#
# Man pages
#
.if ${PORT_OPTIONS:MMANPAGES}
ALL_TARGET+=	nroff-doc
INSTALL_ARGS+=	-nroff-path ${STAGEDIR}${PREFIX}/man/mann
PLIST_SUB+=	MAN=""
.else
INSTALL_ARGS+=	-no-nroff
PLIST_SUB+=	MAN="@comment "
.endif

#
# HTML documentation
#
.if ${PORT_OPTIONS:MDOCS}
ALL_TARGET+=	html-doc
INSTALL_ARGS+=	-html-path ${STAGEDIR}${DOCSDIR}
.else
INSTALL_ARGS+=	-no-html
.endif

post-patch:
#
# 	Ensure, the detailed output of vendors' self-tests is
# 	available in addition to the pretty progress report:
#
	${REINPLACE_CMD} -e 's,test run,test run -l testlog,' \
		-e 's,$$(libdir)/@PACKAGE@@VERSION@,$$(libdir)/@PACKAGE@,' \
		${WRKSRC}/Makefile.in
	${FIND} ${WRKSRC}/apps -type f ! -name "*.man" | ${XARGS} \
	   ${REINPLACE_CMD} -e 's,exec tclsh,exec ${TCLSH},' -e 's,/usr/bin/env tclsh,${TCLSH},'
#
# 	patch(1) adds a newline at eof, so we need to remove it here
#
	${AWK} 'NR > 1 { print h } { h = $$0 } END { ORS = ""; print h }' \
	   ${WRKSRC}/modules/doctools/tests/text/04 > ${WRKSRC}/modules/doctools/tests/text/04.new
	${MV} ${WRKSRC}/modules/doctools/tests/text/04.new ${WRKSRC}/modules/doctools/tests/text/04
#
#	man pages have the .tcllib suffix, so there's no need to have a
#	tcllib_ prefix too
#
	cd ${WRKSRC} && \
	for man in `${FIND} . -name "tcllib_*.man"`; do \
	    ${MV} $$man `echo $$man | ${SED} -e 's|tcllib_||'`; \
	done && \
	for man in `${FIND} . -name "tcllib_*.n"`; do \
	    ${MV} $$man `echo $$man | ${SED} -e 's|tcllib_||'`; \
	done

#
#	add the .tcllib suffix to man pages
#
	cd ${WRKSRC} && \
	for man in `${FIND} . -name "*.man"`; do \
	    ${MV} $$man `echo $$man | ${SED} -e 's|man$$|tcllib.man|'`; \
	done && \
	for man in `${FIND} . -name "*.n"`; do \
	    ${MV} $$man `echo $$man | ${SED} -e 's|n$$|tcllib.n|'`; \
	done
	cd ${WRKSRC}/modules/json/c && ${YACC} -b json json.y

do-install:
	cd ${WRKSRC} && ${TCLSH} ./installer.tcl ${INSTALL_ARGS}
	${RM} ${WRKSRC}/modules/tcllibc/license.terms
	${CP} -Rp ${WRKSRC}/modules/tcllibc ${STAGEDIR}${PREFIX}/lib/tcllib/

test check regression-test: build
	cd ${WRKSRC} && ${SETENV} LANG=C LC_ALL=C DISPLAY= ${MAKE} test

.include <bsd.port.mk>
