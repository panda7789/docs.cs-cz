---
title: 'Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby'
ms.date: 03/30/2017
ms.assetid: 56ffcb99-fff0-4479-aca0-e3909009f605
ms.openlocfilehash: 3fe09699304de42ed00312f50f3b9e0edb20615d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298926"
---
# <a name="how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically"></a>Postupy: Použití třídy MetadataResolver k dynamickému získání metadat vazby
V tomto tématu se dozvíte, jak používat <xref:System.ServiceModel.Description.MetadataResolver> třídy dynamicky získání metadat vazby.  
  
### <a name="to-dynamically-obtain-binding-metadata"></a>Dynamicky získání metadat vazby  
  
1. Vytvoření <xref:System.ServiceModel.EndpointAddress> objektu s adresou koncový bod metadat.  
  
    ```  
    EndpointAddress metaAddress  
      = new EndpointAddress(new   Uri("http://localhost:8080/SampleService/mex"));  
    ```  
  
2. Volání <xref:System.ServiceModel.Description.MetadataResolver.Resolve%28System.Type%2CSystem.ServiceModel.EndpointAddress%29>, tím se předá typ služby a adresu koncového bodu metadat. Vrátí kolekce koncových bodů, které implementují zadaný kontraktu. Pouze informace o vazbě je naimportované z metadat; informace o smlouvě neimportujeme. Zadaná smlouva je místo toho použít.  
  
    ```  
    ServiceEndpointCollection endpoints = MetadataResolver.Resolve(typeof(SampleServiceClient),metaAddress);  
    ```  
  
3. Potom můžete iterovat kolekce koncové body služby chcete extrahovat informace o vazbě, které potřebujete. Následující kód prochází koncových bodů, vytvoří klientského objektu služby, který předává vazbu a adresu přidruženou k aktuální koncový bod a potom volá metodu pro službu.  
  
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
