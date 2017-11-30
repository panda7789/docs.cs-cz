---
title: "Formáty metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d250b57282d24780dcdd1e045f18d7528bd86a90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-formats"></a>Formáty metadat
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]podporuje formáty metadat v následující tabulce.  
  
## <a name="metadata-specifications-and-usage"></a>Specifikace metadat a využití  
  
|Protokol|Specifikace a využití|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Webové služby popis Language (WSDL) používá k popisu služby.|  
|XML schéma|[XML schéma část 2: Datové typy druhé vydání](http://go.microsoft.com/fwlink/?LinkId=94861) a [XML schéma část 1: struktury druhé vydání](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]k popisu typy dat používaných v zprávy používá schéma XML.|  
|Zásady WS|[Webové služby zásady 1.2 - Framework (WS-Policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Webové služby zásady 1.5 – Framework](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá WS-Policy 1.2 nebo 1,5 specifikace s kontrolní výrazy specifické pro doménu k popisu služby požadavky a možnosti.|  
|Zásady WS příloh|[Webové služby zásady 1.2 - přílohy (WS-PolicyAttachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje WS-Policy přílohy připojit výrazy zásad na různé obory ve schématu WSDL.|  
|WS Metadata Exchange|[Webové služby Metadata Exchange (WS-MetadataExchange) verze 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-zásad.|  
|WS adresování vazby pro WSDL|[Webové služby adresování 1.0 - vazby WSDL](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje WS-Addressing vazba pro WSDL připojit informace o přidělování v jazyce WSDL.|  
  
## <a name="see-also"></a>Viz také  
 [Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL a zásady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
