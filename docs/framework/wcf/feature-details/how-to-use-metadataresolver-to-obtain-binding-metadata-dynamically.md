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
ms.workload: dotnet
ms.openlocfilehash: 640d053e0186766e5acdbef692f4e7fae59337b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby
Toto téma ukazuje, jak používat <xref:System.ServiceModel.Description.MetadataResolver> třída dynamicky získání metadat vazby.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Dynamicky získání metadat vazby  
  
1.  Vytvoření <xref:System.ServiceModel.EndpointAddress> objekt s adresou koncový bod metadat.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  Volání <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, která předá typ služby a adresa koncového bodu metadat. Vrátí kolekci koncových bodů, které implementují zadané kontrakt. Pouze informace o vazbě je importovat z metadat; informace o smlouvě není importován. Zadaný kontrakt bude místo něj použita.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  Můžete pak iteraci prostřednictvím kolekce koncových bodů služby extrahovat informace o vazbě, které potřebujete. Následující kód iteruje koncových bodů, vytvoří objekt služby klienta, který předává v vazby a adresa přidružená aktuální koncový bod a pak zavolá metodu ve službě.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
