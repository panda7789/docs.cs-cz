---
title: Koncepty zabezpečení používané ve službě WCF
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: 2dd820d4b6ba38f194074465ac7c1f40289fd928
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541791"
---
# <a name="security-concepts-used-in-wcf"></a>Koncepty zabezpečení používané ve službě WCF
Zabezpečení Windows Communication Foundation (WCF) je postavené na koncepty již používán a nasadit v různých zabezpečení infrastruktury.  
  
 WCF podporuje některé z těchto infrastruktury, jako je například vrstvy SSL (Secure Sockets) přes HTTP (HTTPS). Ale WCF jde nad rámec Podpora stávajících infrastruktur zabezpečení implementací novější standardy interoperabilní zabezpečení (jako je WS-Security) za kódováním protokolu SOAP zprávy. Ať používáte existující mechanismy nebo nové interoperabilní standardy, principy zabezpečení obě jsou stejné. Principy Principy stávajících infrastruktur a novější standardy, které je zásadním implementace nejlepší model zabezpečení pro aplikaci.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Úvod do zabezpečení pro webové služby WCF  
 Skupina Microsoft Patterns and Practices napsal podrobný dokument White Paper o na doprovodné materiály zabezpečení WCF, která je k dispozici ke stažení zde: [Příručka zabezpečení WCF](https://go.microsoft.com/fwlink/?LinkId=210210). Tento dokument White Paper popisuje základní bezpečnostní principy, jejich vztah k webové služby, klíčové koncepty zabezpečení WCF, scénářích s intranetem aplikace a scénáře aplikací Internetu.  
  
## <a name="industry-wide-security-specifications"></a>Specifikace globální zabezpečení  
  
### <a name="public-key-infrastructure"></a>Infrastruktura veřejných klíčů  
 Infrastruktura veřejných klíčů (PKI) je systém digitální certifikáty, certifikační autority a další registrační autority, které ověřují jednotlivých účastníků v transakci elektronických prostřednictvím kryptografii využívající veřejného klíče. Další informace najdete v tématu [systému Windows Server 2008 R2 Certificate Services](https://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Protokol Kerberos  
 *Protokol Kerberos* je specifikace pro vytvoření mechanismus zabezpečení, která ověřuje uživatele v doméně Windows. Umožňuje uživateli vytvořit zabezpečené kontext s jinými entitami v rámci domény. Windows 2000 a novějším platformy pomocí protokolu Kerberos ve výchozím nastavení. Principy mechanismy systému je užitečné, když vytvoření služby, který bude komunikovat s intranetoví klienti. Kromě toho od *webových služeb zabezpečení pomocí protokolu Kerberos vazby* je široce publikováno, můžete použít protokol Kerberos ke komunikaci s klienty v Internetu (to znamená, protokolu Kerberos je interoperabilní). Další informace o tom, jak se implementují protokol Kerberos ve Windows najdete v tématu [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>Certifikáty X.509  
 Certifikáty X.509 jsou formou primární přihlašovacích údajů používaných pro zabezpečení aplikace. Další informace o X.509 certifikátů najdete v části [veřejný klíč certifikátů X.509](https://go.microsoft.com/fwlink/?LinkId=210213). V úložišti certifikátů ukládají certifikáty X.509. Počítač se systémem Windows má několik druhů úložišť certifikátů, každý s jiným způsobem. Další informace o různých úložištích, naleznete v tématu [úložišť certifikátů](https://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>Webové služby specifikace zabezpečení  
 Mnoho běžně používaných webových služeb zabezpečení specifikace podporu vazeb definovaných systémem. Kompletní seznam systémových vazeb a specifikací webových služeb podporují, najdete v tématu: [Protokoly webových služeb podporované vazbami interoperability poskytnutými systémem](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Mechanismy řízení přístupu  
 WCF poskytuje několik způsobů, jak řídit přístup ke službě nebo operaci. Mezi nimi jsou  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  Zprostředkovatel členství technologie ASP.NET  
  
3.  Zprostředkovatele rolí ASP.NET  
  
4.  Správce autorizací  
  
5.  Modelem identity  
  
 Další informace o těchto tématech naleznete v tématu [mechanismy řízení přístupu](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Viz také:
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
