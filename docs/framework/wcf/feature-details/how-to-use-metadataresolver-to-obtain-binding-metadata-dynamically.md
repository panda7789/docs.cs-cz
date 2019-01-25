---
title: 'Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 9887f74902a1f324f57e39a61a48b5826127cba9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735971"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby
V tomto tématu se dozvíte, jak používat <xref:System.ServiceModel.Description.MetadataResolver> třídy dynamicky získání metadat vazby.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Dynamicky získání metadat vazby  
  
1.  Vytvoření <xref:System.ServiceModel.EndpointAddress> objektu s adresou koncový bod metadat.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2.  Volání <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, tím se předá typ služby a adresu koncového bodu metadat. Vrátí kolekce koncových bodů, které implementují zadaný kontraktu. Pouze informace o vazbě je naimportované z metadat; informace o smlouvě neimportujeme. Zadaná smlouva je místo toho použít.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3.  Potom můžete iterovat kolekce koncové body služby chcete extrahovat informace o vazbě, které potřebujete. Následující kód prochází koncových bodů, vytvoří klientského objektu služby, který předává vazbu a adresu přidruženou k aktuální koncový bod a potom volá metodu pro službu.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Metadata](../../../../docs/framework/wcf/feature-details/metadata.md)
