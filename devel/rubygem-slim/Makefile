# $FreeBSD$

PORTNAME=	slim
PORTVERSION=	3.0.3
CATEGORIES=	devel rubygems
MASTER_SITES=	RG

MAINTAINER=	ruby@FreeBSD.org
COMMENT=	Template language whose goal is reduce the syntax to essential parts

LICENSE=	MIT

RUN_DEPENDS=	rubygem-temple>=0.7.3:${PORTSDIR}/devel/rubygem-temple \
		rubygem-tilt>=1.3.3:${PORTSDIR}/devel/rubygem-tilt

USE_RUBY=	yes
USE_RUBYGEMS=	yes
RUBYGEM_AUTOPLIST=	yes

PLIST_FILES+=	bin/slimrb

.include <bsd.port.mk>
