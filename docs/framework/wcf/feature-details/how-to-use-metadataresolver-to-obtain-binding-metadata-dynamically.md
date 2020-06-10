---
title: 'Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 98fe4977f270b008c51039af19261ca86b8d6642
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601124"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="804a5-102">Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby</span><span class="sxs-lookup"><span data-stu-id="804a5-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="804a5-103">V tomto tématu se dozvíte, jak pomocí <xref:System.ServiceModel.Description.MetadataResolver> třídy dynamicky získat metadata vazby.</span><span class="sxs-lookup"><span data-stu-id="804a5-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="804a5-104">Chcete-li dynamicky získat metadata vazby</span><span class="sxs-lookup"><span data-stu-id="804a5-104">To dynamically obtain binding metadata</span></span>  
  
1. <span data-ttu-id="804a5-105">Vytvořte <xref:System.ServiceModel.EndpointAddress> objekt s adresou koncového bodu metadat.</span><span class="sxs-lookup"><span data-stu-id="804a5-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. <span data-ttu-id="804a5-106">Volání <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29> , které předává typ služby a adresu koncového bodu metadat.</span><span class="sxs-lookup"><span data-stu-id="804a5-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="804a5-107">Vrátí kolekci koncových bodů, které implementují zadaný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="804a5-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="804a5-108">Z metadat se importují jenom informace o vazbě. informace o kontraktu se neimportují.</span><span class="sxs-lookup"><span data-stu-id="804a5-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="804a5-109">Místo toho se použije zadaný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="804a5-109">The supplied contract is used instead.</span></span>  
  
    ```csharp  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. <span data-ttu-id="804a5-110">Pak můžete iterovat pomocí kolekce koncových bodů služby a extrahovat informace o vazbě, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="804a5-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="804a5-111">Následující kód projde koncovými body, vytvoří objekt klienta služby, který projde vazbou a adresou přidruženou k aktuálnímu koncovému bodu, a pak zavolá metodu služby.</span><span class="sxs-lookup"><span data-stu-id="804a5-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
    ```csharp  
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
  
## <a name="see-also"></a><span data-ttu-id="804a5-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="804a5-112">See also</span></span>

- [<span data-ttu-id="804a5-113">Metadata</span><span class="sxs-lookup"><span data-stu-id="804a5-113">Metadata</span></span>](metadata.md)
