# Created by: Philippe Audeoud <jadawin@tuxaco.net>
# $FreeBSD$

PORTNAME=	ampache
PORTVERSION=	3.8.1
#PORTREVISION=	1
CATEGORIES=	audio www
MASTER_SITES=	GH

MAINTAINER=	git@johnko.ca
COMMENT=	Web-based Audio file manager

LICENSE=	AGPLv3

USE_GITHUB=	yes
GH_ACCOUNT=	ampache
GH_TAGNAME=	${PORTVERSION}

USE_PHP=	mysql pcre session iconv hash gettext mbstring filter xml
WANT_PHP_WEB=	yes

NO_BUILD=	yes
USES=		gettext

PKGDEINSTALL=	${WRKDIR}/pkg-deinstall
PKGMESSAGE=	${WRKDIR}/pkg-message
SUB_FILES=	pkg-message pkg-deinstall
PLIST_SUB=	WWWDIR=${WWWDIR} \
		WWWOWN=${WWWOWN} \
		WWWGRP=${WWWGRP}

PORTDOCS=	README.md

OPTIONS_DEFINE=	DOCS

do-install:
	@${MKDIR} ${STAGEDIR}${WWWDIR}
	${INSTALL_MAN} ${WRKSRC}/docs/man/man1/ampache.1 ${STAGEDIR}${MAN1PREFIX}/man/man1
	${MKDIR} ${STAGEDIR}${DOCSDIR}
.for doc in ${PORTDOCS}
	${INSTALL_DATA} ${WRKSRC}/${doc} ${STAGEDIR}${DOCSDIR}
.endfor
	(cd ${WRKSRC} && ${COPYTREE_SHARE} \* ${STAGEDIR}${WWWDIR} "! -name *.orig")

.include <bsd.port.mk>
