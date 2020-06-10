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
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby
V tomto tématu se dozvíte, jak pomocí <xref:System.ServiceModel.Description.MetadataResolver> třídy dynamicky získat metadata vazby.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Chcete-li dynamicky získat metadata vazby  
  
1. Vytvořte <xref:System.ServiceModel.EndpointAddress> objekt s adresou koncového bodu metadat.  
  
    ```csharp
    EndpointAddress metaAddress  
      = new EndpointAddress(new Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. Volání <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29> , které předává typ služby a adresu koncového bodu metadat. Vrátí kolekci koncových bodů, které implementují zadaný kontrakt. Z metadat se importují jenom informace o vazbě. informace o kontraktu se neimportují. Místo toho se použije zadaný kontrakt.  
  
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
  
## <a name="see-also"></a>Viz také

- [Metadata](metadata.md)
