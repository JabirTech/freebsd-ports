# Created by: Tom McLaughlin <tmclaugh@sdf.lonestar.org>
# $FreeBSD$

# Port logic gratuitously stolen from x11-themes/kde-icons-noia by
# lioux@.  If it's not defined here and you think it should be, check
# x11-themes/gnome-icons/bsd.gnome-icons.mk for it.

PORTNAME=	gentoo-test
PORTVERSION=	0.1
PORTREVISION=	3
CATEGORIES=	x11-themes gnome
MASTER_SITES=	GNOME/teams/art.gnome.org/archive/themes/icon
DISTNAME=	ICON-Gentoo-Test

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Gentoo-Test Icons for Gnome

RESTRICTED=	${REASON}

USES=	tar:bzip2
WRKSRC=		"${WRKDIR}/Gentoo-test"

.include "${.CURDIR}/../gnome-icons/bsd.gnome-icons.mk"
.include <bsd.port.mk>
