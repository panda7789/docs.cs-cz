---
title: Rozdíly mezi ověřováním certifikátu služby provedeným Internet Explorerem a WCF
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 08a790dbbc8bc51a1e47bbcbcf90ec7c035bf3df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549782"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="7dc00-102">Rozdíly mezi ověřováním certifikátu služby provedeným Internet Explorerem a WCF</span><span class="sxs-lookup"><span data-stu-id="7dc00-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="7dc00-103">Z důvodu rozdíl mezi způsob, jak aplikace Internet Explorer a Windows Communication Foundation (WCF) ověřit certifikáty služby, pokud se používá protokol HTTPS je možné, že aplikace Internet Explorer, nebudou moct přístup ke stránce nápovědy nebo Web Services Description Language (WSDL) služby i v případě klienta WCF je možné úspěšně odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="7dc00-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="7dc00-104">Důvodem je, že aplikace Internet Explorer zkontroluje, jestli certifikát služby má `ServerAuthentication` ve příznaky použití rozšířeného objekt identifikátory (OID), zatímco WCF nevynucuje těchto omezení.</span><span class="sxs-lookup"><span data-stu-id="7dc00-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="7dc00-105">Pokud aplikace Internet Explorer nejde získat přístup ke stránce nápovědy služby nebo WSDL pro službu, použijte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) přistupuje k metadatům služby.</span><span class="sxs-lookup"><span data-stu-id="7dc00-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dc00-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7dc00-106">See also</span></span>
- [<span data-ttu-id="7dc00-107">Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP</span><span class="sxs-lookup"><span data-stu-id="7dc00-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="7dc00-108">Postupy: Načítání metadat a implementace kompatibilní služby</span><span class="sxs-lookup"><span data-stu-id="7dc00-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
