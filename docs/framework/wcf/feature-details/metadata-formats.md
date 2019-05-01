---
title: Formáty metadat
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: 55f68f4b56e50b19da19ecc941e9ec537b846006
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038568"
---
# <a name="metadata-formats"></a>Formáty metadat
Windows Communication Foundation (WCF) podporuje formáty metadat v následující tabulce.  
  
## <a name="metadata-specifications-and-usage"></a>Specifikace metadat a využití  
  
|Protocol (Protokol)|Specifikace a využití|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF webové služby WSDL (Description Language) používá k popisu služby.|  
|XML schéma|[XML schématu část 2: Datové typy druhé vydání](https://go.microsoft.com/fwlink/?LinkId=94861) a [XML schématu část 1: Struktury druhé vydání](https://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> WCF používá schéma XML pro popis datových typů používaných pro zprávy.|  
|Zásada WS|[Webové služby zásady 1.2 – rozhraní (WS-Policy)](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Webové služby zásady 1.5 – rozhraní](https://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF pomocí WS-Policy 1.2 nebo 1.5 specifikace pomocí kontrolních výrazů specifického pro doménu popisují požadavky na služby a funkce.|  
|Zásada WS přílohy|[Webové služby zásady 1.2 – přílohy (WS-PolicyAttachment)](https://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> WCF implementuje přílohami WS-Policy připojit výrazy zásad v různých oborech v jazyce WSDL.|  
|WS Metadata Exchange|[Webové služby Metadata Exchange (WS-MetadataExchange) verze 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-Policy.|  
|Vazby pro WSDL adresování WS|[Webové služby adresování 1.0 - Vazba WSDL](https://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> WCF implementuje WS-Addressing vazby pro WSDL připojit adresování informace v jazyce WSDL.|  
  
## <a name="see-also"></a>Viz také:

- [Protokoly webových služeb podporované vazbami interoperability poskytnutými systémem](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL a zásady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
