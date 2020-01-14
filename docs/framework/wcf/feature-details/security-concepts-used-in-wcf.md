---
title: Koncepty zabezpečení používané ve službě WCF
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: ce6dc6f5cb8680d6228e21206afdc3aa33085e7d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938126"
---
# <a name="security-concepts-used-in-wcf"></a>Koncepty zabezpečení používané ve službě WCF
Zabezpečení Windows Communication Foundation (WCF) je postavené na základě konceptů, které se už používají a nasazují v různých bezpečnostních infrastrukturách.  
  
 WCF podporuje některé z těchto infrastruktur, jako je například SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP (HTTPS). Nicméně služba WCF překračuje podporu stávajících infrastruktur zabezpečení tím, že implementuje novější standardy zabezpečení vzájemně interoperabilních standardů (například WS-Security) prostřednictvím zpráv kódovaných v protokolu SOAP. Bez ohledu na to, jestli používáte stávající mechanismy nebo nové interoperabilní standardy, jsou koncepce zabezpečení za obou stejných. Princip konceptů za stávajícími infrastrukturami a novějších standardů je centrální pro implementaci nejlepšího modelu zabezpečení pro aplikaci.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Úvod do zabezpečení pro webové služby WCF  
 Skupina Microsoft Patterns and Practices vytvořila podrobný dokument white paper o zásadách zabezpečení služby WCF, které je k dispozici ke stažení zde: [Příručka zabezpečení WCF](https://go.microsoft.com/fwlink/?LinkId=210210). Tento dokument white paper popisuje základní koncepty zabezpečení, které se vztahují na webové služby, klíčové koncepty zabezpečení WCF, scénáře intranetové aplikace a scénáře internetových aplikací.  
  
## <a name="industry-wide-security-specifications"></a>Specifikace zabezpečení v celém oboru  
  
### <a name="public-key-infrastructure"></a>Infrastruktura veřejných klíčů  
 Infrastruktura veřejných klíčů (PKI) je systém digitálních certifikátů, certifikačních autorit a dalších registračních autorit, které ověřují a ověřují každou stranu zapojenou do elektronické transakce pomocí kryptografie s veřejným klíčem. Další informace najdete v tématu [Certifikační služba Windows serveru 2008 R2](https://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Protokol Kerberos  
 *Protokol Kerberos* je specifikace pro vytvoření mechanismu zabezpečení, který ověřuje uživatele v doméně systému Windows. Umožňuje uživateli vytvořit zabezpečený kontext s jinými entitami v rámci domény. Platformy Windows 2000 a novější používají ve výchozím nastavení protokol Kerberos. Porozumění mechanismům systému je užitečné při vytváření služby, která bude spolupracovat s intranetovým klientem. Kromě toho, vzhledem specifikace Web Services Security k tomu, že je *vazba protokolu Kerberos* v provozu široce publikovaná, můžete k komunikaci s internetovými klienty použít protokol Kerberos (to znamená, že je možné komunikovat s protokolem Kerberos). Další informace o implementaci protokolu Kerberos v systému Windows najdete v tématu [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>Certifikáty X. 509  
 Certifikáty X. 509 jsou primárním formulářem přihlašovacích údajů, který se používá v aplikacích zabezpečení. Další informace o certifikátech X. 509 najdete v tématu [certifikáty s veřejným klíčem x. 509](https://go.microsoft.com/fwlink/?LinkId=210213). Certifikáty X. 509 se ukládají v úložišti certifikátů. Počítač se systémem Windows má několik druhů úložišť certifikátů, z nichž každý má jiný účel. Další informace o různých úložištích najdete v tématu [úložiště certifikátů](https://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>Specifikace specifikace Web Services Security  
 Vazby definované systémem podporují mnoho běžně používaných specifikací zabezpečení webových služeb. Úplný seznam vazeb poskytovaných systémem a specifikací pro webové služby, které podporují, najdete v tématu [protokoly webových služeb podporované vazbami interoperability poskytovanými systémem](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md) .  
  
## <a name="access-control-mechanisms"></a>Mechanismy řízení přístupu  
 Služba WCF nabízí několik způsobů, jak řídit přístup ke službě nebo operaci. Mezi nimi patří  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. Poskytovatel členství ASP.NET  
  
3. Poskytovatel rolí ASP.NET  
  
4. Správce autorizací  
  
5. Model identity  
  
 Další informace o těchto tématech najdete v [Access Controlch mechanismech](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md) .  
  
## <a name="see-also"></a>Viz také:

- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
