# Created by: Dmitry Marakasov <amdmi3@FreeBSD.org>
# $FreeBSD$

PORTNAME=	git-bzr-ng
PORTVERSION=	git20140423
CATEGORIES=	devel

MAINTAINER=	amdmi3@FreeBSD.org
COMMENT=	Bi-directional git to bzr bridge

LICENSE=	BSD3CLAUSE
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	git:${PORTSDIR}/devel/git \
		bzr:${PORTSDIR}/devel/bzr \
		${PYTHON_SITELIBDIR}/bzrlib/plugins/fastimport/__init__.py:${PORTSDIR}/devel/bzr-fastimport

USE_GITHUB=	yes
GH_ACCOUNT=	termie
GH_TAGNAME=	9878a30

USES=		python:2,run
NO_BUILD=	yes
PLIST_FILES=	libexec/git-core/git-bzr
PORTDOCS=	*

OPTIONS_DEFINE=	DOCS

do-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/libexec/git-core
	${INSTALL_SCRIPT} ${WRKSRC}/git-bzr ${STAGEDIR}${PREFIX}/libexec/git-core/
	${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${WRKSRC}/README.rst ${STAGEDIR}${DOCSDIR}/

.include <bsd.port.mk>
