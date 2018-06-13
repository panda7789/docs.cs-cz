---
title: Rozdíly mezi ověřováním certifikátu služby provedeným Internet Explorerem a WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: ecc2b16eae5428e305f5f6096d6d7994256d86c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488683"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Rozdíly mezi ověřováním certifikátu služby provedeným Internet Explorerem a WCF
Kvůli rozdílu mezi způsobu, jakým aplikace Internet Explorer a Windows Communication Foundation (WCF) ověřují certifikáty služby, pokud se používá protokol HTTPS je možné, že Internet Explorer, nebude možné pro přístup ke stránce nápovědy nebo Web Services Description Language (WSDL) služby Přestože klienta WCF, bude moct úspěšně odesílání zpráv do koncových bodů služby. Důvodem je, že Internet Explorer kontroluje, zda certifikát služby má `ServerAuthentication` objekt identifikátory (OID) v rozšířené použití příznaky, zatímco WCF nevynucuje takových omezení. Pokud se nepodařilo otevřít stránku nápovědy služby nebo WSDL pro službu Internet Explorer, použijte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) přístup k metadatům služby.  
  
## <a name="see-also"></a>Viz také  
 [Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [Postupy: Načítání metadat a implementace kompatibilní služby](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
