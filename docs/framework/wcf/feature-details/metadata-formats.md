---
title: Formáty metadat
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a3c6b1f551d1bff8c68a91f33e62df289d2078cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493435"
---
# <a name="metadata-formats"></a>Formáty metadat
Windows Communication Foundation (WCF) podporuje formáty metadat v následující tabulce.  
  
## <a name="metadata-specifications-and-usage"></a>Specifikace metadat a využití  
  
|Protokol|Specifikace a využití|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF Web Services popis Language (WSDL) používá k popisu služby.|  
|XML schéma|[XML schéma část 2: Datové typy druhé vydání](http://go.microsoft.com/fwlink/?LinkId=94861) a [XML schéma část 1: struktury druhé vydání](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> WCF popisují typy dat používaných v zpráv pomocí schématu XML.|  
|Zásady WS|[Webové služby zásady 1.2 - Framework (WS-Policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Webové služby zásady 1.5 – Framework](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF používá WS-Policy 1.2 nebo 1,5 specifikace s kontrolní výrazy specifické pro doménu k popisu služby požadavky a možnosti.|  
|Zásady WS příloh|[Webové služby zásady 1.2 - přílohy (WS-PolicyAttachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> WCF implementuje WS-Policy přílohy připojit výrazy zásad na různé obory ve schématu WSDL.|  
|WS Metadata Exchange|[Webové služby Metadata Exchange (WS-MetadataExchange) verze 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-zásad.|  
|WS adresování vazby pro WSDL|[Webové služby adresování 1.0 - vazby WSDL](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> WCF implementuje WS-Addressing vazba pro WSDL připojit informace o přidělování v jazyce WSDL.|  
  
## <a name="see-also"></a>Viz také  
 [Protokoly webových služeb podporované vazbami interoperability poskytnutými systémem](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL a zásady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
