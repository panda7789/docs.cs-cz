---
title: Serializace ve formátu Json s programováním na úrovni zpráv
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 36459dbc0ddee883678a98a27f9abb74fde78e86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184499"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializace ve formátu Json s programováním na úrovni zpráv
WCF podporuje serializaci dat ve formátu JSON. Toto téma popisuje, jak sdělit WCF serializovat typy pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Programování zadali zpráv  
 Používá <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> se při <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> je použita operace služby. Oba tyto atributy umožňují zadat `RequestFormat` `ResponseFormat`a . Chcete-li použít JSON pro požadavky a odpovědi. nastavte obě tyto `WebMessageFormat.Json`na .  Chcete-li použít službu <xref:System.ServiceModel.WebHttpBinding>JSON, musíte použít <xref:System.ServiceModel.Description.WebHttpBehavior>rozhraní , které automaticky konfiguruje rozhraní . Další informace o serializaci WCF naleznete [v tématu Serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Další informace o JSON a WCF naleznete v tématu [Service Station - Úvod do restful služby s WCF](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).  
  
> [!IMPORTANT]
> Použití JSON vyžaduje <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> použití a které nepodporují komunikaci SOAP. Služby, které <xref:System.ServiceModel.WebHttpBinding> komunikují s nepodporují vystavení metadat služby, takže nebudete moci použít Visual Studio přidat service reference funkce nebo svcutil příkazový řádek nástroj pro generování proxy serveru na straně klienta. Další informace o tom, jak můžete <xref:System.ServiceModel.WebHttpBinding>programově volat služby, které používají , naleznete v [tématu Jak využívat služby REST services s WCF](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).  
  
## <a name="untyped-message-programming"></a>Programování zpráv bez typu  
 Při práci přímo s netypovými objekty Message je nutné explicitně nastavit vlastnosti zprávy bez typu, aby byla serializovat jako JSON. Následující fragment kódu ukazuje, jak to provést.  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Viz také

- [Integrace jazyka AJAX a podpora JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [Samostatná serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Serializace JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
