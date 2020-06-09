---
title: Formáty metadat
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a74a57843beaba09b969678a34cad3ad8bed7050
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598837"
---
# <a name="metadata-formats"></a>Formáty metadat
Windows Communication Foundation (WCF) podporuje formáty metadat v následující tabulce.  
  
## <a name="metadata-specifications-and-usage"></a>Specifikace a využití metadat  
  
|Protocol (Protokol)|Specifikace a použití|  
|--------------|-----------------------------|  
|WSDL 1,1|[Jazyk WSDL (Web Services Description Language) 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF používá k popisu služeb službu Web Services Description Language (WSDL).|  
|XML schéma|[Schéma XML – část 2: DataTypes Second Edition](https://www.w3.org/TR/2004/REC-xmlschema-2-20041028/) a [XML Schema Part 1: struktury druhé edice](https://www.w3.org/TR/2004/REC-xmlschema-1-20041028/)<br /><br /> WCF používá schéma XML k popisu datových typů používaných ve zprávách.|  
|Zásada WS|[Zásady webových služeb 1,2-Framework (WS-Policy)](https://www.w3.org/Submission/WS-Policy/)<br /><br /> [Zásady webových služeb 1,5 – architektura](https://www.w3.org/TR/ws-policy/)<br /><br /> WCF používá specifikace WS-Policy 1,2 nebo 1,5 s kontrolními výrazy specifickými pro doménu k popisu požadavků a možností služby.|  
|Přílohy zásad WS|[Zásady webových služeb 1,2 – Příloha (WS-PolicyAttachment)](https://www.w3.org/Submission/WS-PolicyAttachment/)<br /><br /> WCF implementuje přílohy WS-Policy pro připojení výrazů zásad v různých oborech WSDL.|  
|WS Metadata Exchange|[Výměna metadat služby Web Services (WS-MetadataExchange) verze 1,1](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
|Vazba adres WS pro WSDL|[Webové služby Addressing 1,0 – Vazba WSDL](https://www.w3.org/TR/ws-addr-wsdl/)<br /><br /> WCF implementuje vazby WS-Addressing pro WSDL pro připojení informací o adresách v jazyce WSDL.|  
  
## <a name="see-also"></a>Viz také

- [Protokoly webových služeb podporované vazbami interoperability poskytnutými systémem](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL a zásady](wsdl-and-policy.md)
