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
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="508f9-102">Rozdíly mezi ověřením certifikátu služby provedeným Internet Explorerem a WCF</span><span class="sxs-lookup"><span data-stu-id="508f9-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="508f9-103">Vzhledem k tomu, že aplikace Internet Explorer a Windows Communication Foundation (WCF) ověřuje certifikáty služeb při použití protokolu HTTPS, je možné, že Internet Explorer nebude mít přístup ke stránce s nápovědě nebo k jazyku WSDL (Web Services Description Language), a to i v případě, že klient WCF může úspěšně odesílat zprávy do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="508f9-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="508f9-104">Je to proto, že aplikace Internet Explorer kontroluje, zda má certifikát služby `ServerAuthentication` identifikátory objektů (OID) v příznacích rozšířeného použití, zatímco služba WCF toto omezení nevynutila.</span><span class="sxs-lookup"><span data-stu-id="508f9-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="508f9-105">Pokud Internet Explorer nemůže získat přístup ke stránce s nápovědu služby nebo ke WSDL pro službu, použijte nástroj pro přístup k metadatům služby [(Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="508f9-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="508f9-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="508f9-106">See also</span></span>

- [<span data-ttu-id="508f9-107">Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP</span><span class="sxs-lookup"><span data-stu-id="508f9-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="508f9-108">Postupy: Načítání metadat a implementace kompatibilní služby</span><span class="sxs-lookup"><span data-stu-id="508f9-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
