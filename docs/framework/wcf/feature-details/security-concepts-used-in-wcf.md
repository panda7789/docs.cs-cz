---
title: Koncepty zabezpečení používané ve službě WCF
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ac76f1742ab72de9f5180d1ea2fcbc668ec2140c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497630"
---
# <a name="security-concepts-used-in-wcf"></a>Koncepty zabezpečení používané ve službě WCF
Zabezpečení Windows Communication Foundation (WCF) je založena na koncepty již používán a nasadit v různých zabezpečení infrastruktury.  
  
 WCF podporuje některé z těchto infrastruktury, jako je například vrstvy SSL (Secure Sockets) přes protokol HTTP (HTTPS). Ale WCF překročí podpora existující infrastruktury zabezpečení implementací novější standardy, umožňuje vzájemnou spolupráci zabezpečení (jako je WS-Security) přes kódováním protokolu SOAP zprávy. Ať používáte existující mechanismy nebo nové umožňuje vzájemnou spolupráci standardů, koncepty zabezpečení za obě jsou stejné. Vysvětlení pojmů týkajících se stávající infrastruktury a novější standardy je důležitá pro implementaci doporučené model zabezpečení pro aplikace.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Úvod do zabezpečení pro webové služby WCF  
 Skupina Microsoft Patterns and Practices napsali hlouběji dokumentu na doprovodné materiály zabezpečení WCF, která je k dispozici ke stažení zde: [Příručka zabezpečení WCF](http://go.microsoft.com/fwlink/?LinkId=210210). Tento dokument White Paper popisuje základní zabezpečení koncepty, které se vztahují webové služby, klíčové koncepty zabezpečení WCF, scénáře aplikací intranetu a Internetu scénáře aplikací.  
  
## <a name="industry-wide-security-specifications"></a>Specifikace napříč celým průmyslem zabezpečení  
  
### <a name="public-key-infrastructure"></a>Infrastruktura veřejných klíčů  
 Infrastruktury veřejných klíčů (PKI) je systém digitální certifikáty, certifikačních autorit a dalších registračním autoritám, které k ověřování jednotlivých stran zahrnutých v elektronické transakce pomocí kryptografie využívající veřejného klíče. Další informace najdete v tématu [Windows Server 2008 R2 Certificate Services](http://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Protokol Kerberos  
 *Protokol Kerberos* je specifikace pro vytvoření zabezpečení mechanismus, který ověřuje uživatele v doméně systému Windows. Umožňuje uživateli vytvořit kontext zabezpečení s dalšími subjekty, v rámci domény. Windows 2000 a novějších platformy používat protokol Kerberos ve výchozím nastavení. Principy mechanismy systému je užitečné, když vytvoření služby, který bude komunikovat s intranetoví klienti. Kromě toho od *webové služby zabezpečení protokolu Kerberos vazby* je široce publikovali, můžete použít protokol Kerberos ke komunikaci s klienty v Internetu (to znamená, protokol Kerberos je interoperabilní). Další informace o tom, jak implementují protokol Kerberos v systému Windows najdete v tématu [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>X.509 – certifikáty  
 X.509 – certifikáty jsou primární pověření formuláře použít v aplikacích zabezpečení. Další informace o X.509 certifikátů najdete v části [veřejný klíč certifikáty X.509](http://go.microsoft.com/fwlink/?LinkId=210213). X.509 – certifikáty jsou uloženy v úložišti certifikátů. Počítač se systémem Windows má několik druhů úložišť certifikátů, každý s jinému účelu. Další informace o různých obchodů najdete v tématu [úložiště certifikátů](http://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>Webové služby specifikace zabezpečení  
 Vazby definovaná systémem podporují mnoho specifikace zabezpečení běžně používané webové služby. Úplný seznam vazeb poskytovaných systémem a specifikace web services podporují najdete v tématu: [webové služby protokoly podporované vazbami vzájemné spolupráce System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Mechanismy řízení přístupu  
 WCF poskytuje několik způsobů, jak řídit přístup ke službě nebo operace. Mezi nimi jsou  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  Poskytovatele členství prostředí ASP.NET  
  
3.  Zprostředkovatele rolí ASP.NET  
  
4.  Správce autorizací  
  
5.  Modelu identity  
  
 Další informace o těchto tématech naleznete v tématu [mechanismy řízení přístupu](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Viz také  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
