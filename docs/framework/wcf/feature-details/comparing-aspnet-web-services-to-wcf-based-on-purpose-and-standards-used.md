---
title: Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů
ms.date: 03/30/2017
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
ms.openlocfilehash: b27f3516868ec70319ce37fbbd774a29347b0bc8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597576"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů
Webové služby ASP.NET byly vyvinuty pro vytváření aplikací, které odesílají a přijímají zprávy pomocí protokolu SOAP (Simple Object Access Protocol) přes protokol HTTP. Strukturu zpráv lze definovat pomocí schématu XML a je k dispozici nástroj pro usnadnění serializace zpráv do a z .NET Framework objektů. Technologie může automaticky generovat metadata pro popis webových služeb v jazyce WSDL (Web Services Description Language) a druhý nástroj je k dispozici pro generování klientů pro webové služby z rozhraní WSDL.  
  
 WCF slouží k tomu, aby aplikace .NET Framework vyměňovat zprávy s jinými softwarovými entitami. Protokol SOAP je ve výchozím nastavení používán, ale zprávy mohou být v jakémkoli formátu a prostřednictvím libovolného transportního protokolu. Strukturu zpráv lze definovat pomocí schématu XML a existují různé možnosti pro serializaci zpráv do a z .NET Framework objektů. WCF může automaticky generovat metadata pro popis aplikací vytvořených pomocí technologie v jazyce WSDL a zároveň poskytuje nástroj pro generování klientů pro tyto aplikace ze sady WSDL.  
  
 Standardy podporované webovými službami ASP.NET jsou popsány v [výhodách webových služeb XML vytvořených pomocí ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0859ebft(v=vs.100)). Širší seznam standardů podporovaných službou WCF najdete v části [protokoly webových služeb podporované vazbami interoperability poskytované systémem](web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Viz také

- [Porovnání webových služeb ASP.NET s technologií WCF z hlediska vývojových požadavků](comparing-aspnet-web-services-to-wcf-based-on-development.md)
