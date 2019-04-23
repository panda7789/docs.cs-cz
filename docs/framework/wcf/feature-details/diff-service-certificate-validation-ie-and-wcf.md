---
title: Rozdíly mezi ověřením certifikátu služby provedeným Internet Explorerem a WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 0bced548cdc9423d1907de09e8b52ebe078d7c19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225911"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Rozdíly mezi ověřením certifikátu služby provedeným Internet Explorerem a WCF
Z důvodu rozdíl mezi způsob, jak aplikace Internet Explorer a Windows Communication Foundation (WCF) ověřit certifikáty služby, pokud se používá protokol HTTPS je možné, že aplikace Internet Explorer, nebudou moct přístup ke stránce nápovědy nebo Web Services Description Language (WSDL) služby i v případě klienta WCF je možné úspěšně odesílání zpráv do koncových bodů služby. Důvodem je, že aplikace Internet Explorer zkontroluje, jestli certifikát služby má `ServerAuthentication` ve příznaky použití rozšířeného objekt identifikátory (OID), zatímco WCF nevynucuje těchto omezení. Pokud aplikace Internet Explorer nejde získat přístup ke stránce nápovědy služby nebo WSDL pro službu, použijte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) přistupuje k metadatům služby.  
  
## <a name="see-also"></a>Viz také:

- [Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [Postupy: Načítání metadat a implementace kompatibilní služby](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
