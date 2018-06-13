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
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="85ffb-102">Rozdíly mezi ověřováním certifikátu služby provedeným Internet Explorerem a WCF</span><span class="sxs-lookup"><span data-stu-id="85ffb-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="85ffb-103">Kvůli rozdílu mezi způsobu, jakým aplikace Internet Explorer a Windows Communication Foundation (WCF) ověřují certifikáty služby, pokud se používá protokol HTTPS je možné, že Internet Explorer, nebude možné pro přístup ke stránce nápovědy nebo Web Services Description Language (WSDL) služby Přestože klienta WCF, bude moct úspěšně odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="85ffb-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="85ffb-104">Důvodem je, že Internet Explorer kontroluje, zda certifikát služby má `ServerAuthentication` objekt identifikátory (OID) v rozšířené použití příznaky, zatímco WCF nevynucuje takových omezení.</span><span class="sxs-lookup"><span data-stu-id="85ffb-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="85ffb-105">Pokud se nepodařilo otevřít stránku nápovědy služby nebo WSDL pro službu Internet Explorer, použijte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) přístup k metadatům služby.</span><span class="sxs-lookup"><span data-stu-id="85ffb-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ffb-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="85ffb-106">See Also</span></span>  
 [<span data-ttu-id="85ffb-107">Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP</span><span class="sxs-lookup"><span data-stu-id="85ffb-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="85ffb-108">Postupy: Načítání metadat a implementace kompatibilní služby</span><span class="sxs-lookup"><span data-stu-id="85ffb-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
