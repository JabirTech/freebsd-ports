# Created by: Olivier Girard <Olivier.Girard@univ-angers.fr>
# $FreeBSD$

PORTNAME=	Unicode-LineBreak
PORTVERSION=	2014.06
PORTREVISION=	1
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

# blanket update approval granted.
MAINTAINER=	Olivier.Girard@univ-angers.fr
COMMENT=	Unicode-LineBreak package

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-MIME-Charset>=1.006.2:${PORTSDIR}/mail/p5-MIME-Charset
RUN_DEPENDS:=	${BUILD_DEPENDS}

MAKE_JOBS_UNSAFE=	yes

USES=		perl5
USE_PERL5=	configure

CONFIGURE_ARGS=	--with-bundled-sombok

OPTIONS_DEFINE=	THAI

THAI_DESC=	Thai word segmentation support through libthai
THAI_USES=	pkgconfig
THAI_LIB_DEPENDS=	libthai.so:${PORTSDIR}/devel/libthai
THAI_CONFIGURE_OFF=	--disable-libthai

.include <bsd.port.mk>
