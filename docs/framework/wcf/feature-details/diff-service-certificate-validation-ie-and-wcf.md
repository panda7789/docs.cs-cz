---
title: "Rozdíly mezi ověřováním certifikátu služby provedeným Internet Explorerem a WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12e30d9df9d6bb0a9f8776099951e4354d302ebf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Rozdíly mezi ověřováním certifikátu služby provedeným Internet Explorerem a WCF
Z důvodu rozdíl mezi způsob, jakým aplikace Internet Explorer a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ověření certifikátů služby když se používá protokol HTTPS, je možné, že Internet Explorer nebudou mít přístup i k stránku nápovědy nebo webové služby WSDL (Description Language) služby Když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta se bude moct úspěšně odesílání zpráv do koncových bodů služby. Důvodem je, že Internet Explorer kontroluje, zda certifikát služby má `ServerAuthentication` objektu (OID) identifikátory v rozšířené použití příznaky, zatímco [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nevynucuje takových omezení. Pokud se nepodařilo otevřít stránku nápovědy služby nebo WSDL pro službu Internet Explorer, použijte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) přístup k metadatům služby.  
  
## <a name="see-also"></a>Viz také  
 [Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [Postupy: Načítání metadat a implementace kompatibilní služby](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
