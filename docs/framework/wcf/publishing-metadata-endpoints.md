---
title: "Publikování kocových bodů metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0f3f134526fd24a724ba593302ba2bf1f27fa3e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="publishing-metadata-endpoints"></a><span data-ttu-id="a7c1b-102">Publikování kocových bodů metadat</span><span class="sxs-lookup"><span data-stu-id="a7c1b-102">Publishing Metadata Endpoints</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="a7c1b-103">služby publikování metadat tím, že publikujete jeden nebo více koncových bodů metadat.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-103"> services publish metadata by publishing one or more metadata endpoints.</span></span> <span data-ttu-id="a7c1b-104">Publikování metadat služby zpřístupňuje metadata použitím standardizovaných protokolů, jako jsou žádosti o služby WS-MetadataExchange (MEX) a protokolu HTTP nebo získat.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-104">Publishing service metadata makes the metadata available using standardized protocols, such as WS-MetadataExchange (MEX) and HTTP/GET requests.</span></span> <span data-ttu-id="a7c1b-105">Koncové body metadat jsou podobná další koncové body služby, že mají adresy, vazby a kontraktu a mohou být přidány do hostitele služby prostřednictvím konfigurace nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-105">Metadata endpoints are similar to other service endpoints in that they have an address, a binding, and a contract, and they can be added to a service host through configuration or in code.</span></span> <span data-ttu-id="a7c1b-106">Chcete-li povolit publikování kocových bodů metadat, je nutné přidat <xref:System.ServiceModel.Description.ServiceMetadataBehavior> služby chování ke službě.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-106">To enable publishing metadata endpoints, you must add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> service behavior to the service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7c1b-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a7c1b-107">In This Section</span></span>  
 [<span data-ttu-id="a7c1b-108">Postupy: publikování metadat služby promocí konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a7c1b-108">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 <span data-ttu-id="a7c1b-109">Ukazuje, jak nakonfigurovat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby publikovat metadata, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-109">Demonstrates how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to publish metadata so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
 [<span data-ttu-id="a7c1b-110">Postupy: publikování metadat služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="a7c1b-110">How to: Publish Metadata for a Service Using Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 <span data-ttu-id="a7c1b-111">Ukazuje, jak povolit publikování metadat pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby v kódu tak, aby klienti mohou získat metadata pomocí protokolu WS-MetadataExchange nebo žádosti o protokolu HTTP nebo získat pomocí `?wsdl` řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="a7c1b-111">Demonstrates how to enable metadata publishing for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service in code so that clients can retrieve the metadata using a WS-MetadataExchange or an HTTP/GET request using the `?wsdl` query string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c1b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7c1b-112">See Also</span></span>  
 [<span data-ttu-id="a7c1b-113">Publikování metadat</span><span class="sxs-lookup"><span data-stu-id="a7c1b-113">Publishing Metadata</span></span>](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
