---
title: 'Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: dfa36c81bbeb70c1dd981ff91b4efb6d7c423a5c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991621"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby
V <xref:System.ServiceModel.Description.MetadataResolver> tomto tématu se dozvíte, jak pomocí třídy dynamicky získat metadata vazby.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Chcete-li dynamicky získat metadata vazby  
  
1. <xref:System.ServiceModel.EndpointAddress> Vytvořte objekt s adresou koncového bodu metadat.  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. Volání <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, které předává typ služby a adresu koncového bodu metadat. Vrátí kolekci koncových bodů, které implementují zadaný kontrakt. Z metadat se importují jenom informace o vazbě. informace o kontraktu se neimportují. Místo toho se použije zadaný kontrakt.  
  
    ```csharp  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. Pak můžete iterovat pomocí kolekce koncových bodů služby a extrahovat informace o vazbě, které potřebujete. Následující kód projde koncovými body, vytvoří objekt klienta služby, který projde vazbou a adresou přidruženou k aktuálnímu koncovému bodu, a pak zavolá metodu služby.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
