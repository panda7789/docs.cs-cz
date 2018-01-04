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
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="58545-102">Rozdíly mezi ověřováním certifikátu služby provedeným Internet Explorerem a WCF</span><span class="sxs-lookup"><span data-stu-id="58545-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="58545-103">Z důvodu rozdíl mezi způsob, jakým aplikace Internet Explorer a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ověření certifikátů služby když se používá protokol HTTPS, je možné, že Internet Explorer nebudou mít přístup i k stránku nápovědy nebo webové služby WSDL (Description Language) služby Když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta se bude moct úspěšně odesílání zpráv do koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="58545-103">Because of difference between the way Internet Explorer and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="58545-104">Důvodem je, že Internet Explorer kontroluje, zda certifikát služby má `ServerAuthentication` objektu (OID) identifikátory v rozšířené použití příznaky, zatímco [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nevynucuje takových omezení.</span><span class="sxs-lookup"><span data-stu-id="58545-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not enforce such a constraint.</span></span> <span data-ttu-id="58545-105">Pokud se nepodařilo otevřít stránku nápovědy služby nebo WSDL pro službu Internet Explorer, použijte [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) přístup k metadatům služby.</span><span class="sxs-lookup"><span data-stu-id="58545-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58545-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="58545-106">See Also</span></span>  
 [<span data-ttu-id="58545-107">Rozdíly v ověřování certifikátů mezi zabezpečeními HTTPS, SSL přes TCP a SOAP</span><span class="sxs-lookup"><span data-stu-id="58545-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="58545-108">Postupy: Načítání metadat a implementace kompatibilní služby</span><span class="sxs-lookup"><span data-stu-id="58545-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
