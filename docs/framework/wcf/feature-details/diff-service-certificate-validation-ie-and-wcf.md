---
title: Rozdíly mezi ověřením certifikátu služby provedeným Internet Explorerem a WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 151075f2894b895ab90418748df9face3aa70252
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599188"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a>Rozdíly mezi ověřením certifikátu služby provedeným Internet Explorerem a WCF
Vzhledem k tomu, že aplikace Internet Explorer a Windows Communication Foundation (WCF) ověřuje certifikáty služeb při použití protokolu HTTPS, je možné, že Internet Explorer nebude mít přístup ke stránce s nápovědě nebo k jazyku WSDL (Web Services Description Language), a to i v případě, že klient WCF může úspěšně odesílat zprávy do koncových bodů služby. Je to proto, že aplikace Internet Explorer kontroluje, zda má certifikát služby `ServerAuthentication` identifikátory objektů (OID) v příznacích rozšířeného použití, zatímco služba WCF toto omezení nevynutila. Pokud Internet Explorer nemůže získat přístup ke stránce s nápovědu služby nebo ke WSDL pro službu, použijte nástroj pro přístup k metadatům služby [(Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
## <a name="see-also"></a>Viz také

- [Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [Postupy: Načítání metadat a implementace kompatibilní služby](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
