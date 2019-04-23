---
title: 'Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 3fe09699304de42ed00312f50f3b9e0edb20615d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298926"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a><span data-ttu-id="2a73e-102">Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby</span><span class="sxs-lookup"><span data-stu-id="2a73e-102">How to: Use MetadataResolver to Obtain Binding Metadata Dynamically</span></span>
<span data-ttu-id="2a73e-103">V tomto tématu se dozvíte, jak používat <xref:System.ServiceModel.Description.MetadataResolver> třídy dynamicky získání metadat vazby.</span><span class="sxs-lookup"><span data-stu-id="2a73e-103">This topic shows you how to use the <xref:System.ServiceModel.Description.MetadataResolver> class to dynamically obtain binding metadata.</span></span>  
  
### <a name="to-dynamically-obtain-binding-metadata"></a><span data-ttu-id="2a73e-104">Dynamicky získání metadat vazby</span><span class="sxs-lookup"><span data-stu-id="2a73e-104">To dynamically obtain binding metadata</span></span>  
  
1. <span data-ttu-id="2a73e-105">Vytvoření <xref:System.ServiceModel.EndpointAddress> objektu s adresou koncový bod metadat.</span><span class="sxs-lookup"><span data-stu-id="2a73e-105">Create an <xref:System.ServiceModel.EndpointAddress> object with the address of the metadata endpoint.</span></span>  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. <span data-ttu-id="2a73e-106">Volání <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, tím se předá typ služby a adresu koncového bodu metadat.</span><span class="sxs-lookup"><span data-stu-id="2a73e-106">Call <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, which passes in the service type and the metadata endpoint address.</span></span> <span data-ttu-id="2a73e-107">Vrátí kolekce koncových bodů, které implementují zadaný kontraktu.</span><span class="sxs-lookup"><span data-stu-id="2a73e-107">This returns a collection of endpoints that implement the specified contract.</span></span> <span data-ttu-id="2a73e-108">Pouze informace o vazbě je naimportované z metadat; informace o smlouvě neimportujeme.</span><span class="sxs-lookup"><span data-stu-id="2a73e-108">Only binding information is imported from the metadata; contract information is not imported.</span></span> <span data-ttu-id="2a73e-109">Zadaná smlouva je místo toho použít.</span><span class="sxs-lookup"><span data-stu-id="2a73e-109">The supplied contract is used instead.</span></span>  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. <span data-ttu-id="2a73e-110">Potom můžete iterovat kolekce koncové body služby chcete extrahovat informace o vazbě, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="2a73e-110">You can then iterate through the collection of service endpoints to extract the binding information you need.</span></span> <span data-ttu-id="2a73e-111">Následující kód prochází koncových bodů, vytvoří klientského objektu služby, který předává vazbu a adresu přidruženou k aktuální koncový bod a potom volá metodu pro službu.</span><span class="sxs-lookup"><span data-stu-id="2a73e-111">The following code iterates through the endpoints, creates a service client object that passes in the binding and address associated with the current endpoint, and then calls a method on the service.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a73e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a73e-112">See also</span></span>

- [<span data-ttu-id="2a73e-113">Metadata</span><span class="sxs-lookup"><span data-stu-id="2a73e-113">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
