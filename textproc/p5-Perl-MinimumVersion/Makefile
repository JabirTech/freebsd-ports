# $FreeBSD$

PORTNAME=	Perl-MinimumVersion
PORTVERSION=	1.38
PORTREVISION=	1
CATEGORIES=	textproc perl5
MASTER_SITES=	CPAN
PKGNAMEPREFIX=	p5-

MAINTAINER=	lth@FreeBSD.org
COMMENT=	Find a minimum required version of perl for Perl code

LICENSE=	ART10 GPLv1
LICENSE_COMB=	dual

BUILD_DEPENDS=	p5-File-Find-Rule>=0:${PORTSDIR}/devel/p5-File-Find-Rule \
		p5-File-Find-Rule-Perl>=0:${PORTSDIR}/devel/p5-File-Find-Rule-Perl \
		p5-PPI>=1.215:${PORTSDIR}/textproc/p5-PPI \
		p5-PPIx-Regexp>=0.033:${PORTSDIR}/textproc/p5-PPIx-Regexp \
		p5-Perl-Critic>=1.10.4:${PORTSDIR}/textproc/p5-Perl-Critic \
		p5-Params-Util>=0.25:${PORTSDIR}/devel/p5-Params-Util
RUN_DEPENDS:=	${BUILD_DEPENDS}
TEST_DEPENDS=	p5-Test-Script>=0:${PORTSDIR}/devel/p5-Test-Script

USES=		perl5
USE_PERL5=	configure

.include <bsd.port.mk>
