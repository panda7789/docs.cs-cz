---
title: "Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8f3d8245b9d5bf05297b4d1edfba1926d2104ce
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="4d1e8-102">Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby</span><span class="sxs-lookup"><span data-stu-id="4d1e8-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="4d1e8-103">Toto téma ukazuje, jak používat <xref:System.ServiceModel.Description.MetadataResolver> třída dynamicky získání metadat vazby.</span><span class="sxs-lookup"><span data-stu-id="4d1e8-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="4d1e8-104">Dynamicky získání metadat vazby</span><span class="sxs-lookup"><span data-stu-id="4d1e8-104">To dynamically obtain binding metadata</span></span>  
  
1.  <span data-ttu-id="4d1e8-105">Vytvoření <xref:System.ServiceModel.EndpointAddress> objekt s adresou koncový bod metadat.</span><span class="sxs-lookup"><span data-stu-id="4d1e8-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  <span data-ttu-id="4d1e8-106">Volání <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, která předá typ služby a adresa koncového bodu metadat.</span><span class="sxs-lookup"><span data-stu-id="4d1e8-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="4d1e8-107">Vrátí kolekci koncových bodů, které implementují zadané kontrakt.</span><span class="sxs-lookup"><span data-stu-id="4d1e8-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="4d1e8-108">Pouze informace o vazbě je importovat z metadat; informace o smlouvě není importován.</span><span class="sxs-lookup"><span data-stu-id="4d1e8-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="4d1e8-109">Zadaný kontrakt bude místo něj použita.</span><span class="sxs-lookup"><span data-stu-id="4d1e8-109">The supplied contract is used instead.</span></span>  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  <span data-ttu-id="4d1e8-110">Můžete pak iteraci prostřednictvím kolekce koncových bodů služby extrahovat informace o vazbě, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="4d1e8-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="4d1e8-111">Následující kód iteruje koncových bodů, vytvoří objekt služby klienta, který předává v vazby a adresa přidružená aktuální koncový bod a pak zavolá metodu ve službě.</span><span class="sxs-lookup"><span data-stu-id="4d1e8-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
    ```  
    foreach (ServiceEndpoint point in endpoints)  
    {  
       if (point != null)  
       {  
          // Create a new wcfClient using retrieved endpoints.  
          using (wcfClient = new SampleServiceClient(point.Binding, point.Address))  
          {  
             Console.WriteLine(  
               wcfClient.SampleMethod("Client used the "  
               + point.Address.ToString() + " address."));  
          }  
      }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4d1e8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d1e8-112">See Also</span></span>  
 [<span data-ttu-id="4d1e8-113">Metadata</span><span class="sxs-lookup"><span data-stu-id="4d1e8-113">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
