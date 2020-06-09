---
title: Serializace ve formátu Json s programováním na úrovni zpráv
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 854f03e94510b7f02bb1b7660f1e5108fd8faed8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600397"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializace ve formátu Json s programováním na úrovni zpráv
WCF podporuje serializaci dat ve formátu JSON. Toto téma popisuje, jak dát službě WCF pokyn k serializaci vašich typů pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .  
  
## <a name="typed-message-programming"></a>Programování typované zprávy  
 Používá se, když se použije <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.ServiceModel.Web.WebGetAttribute> nebo na <xref:System.ServiceModel.Web.WebInvokeAttribute> operaci služby. Oba tyto atributy umožňují zadat `RequestFormat` a `ResponseFormat` . Pro použití formátu JSON pro žádosti a odpovědi. nastavte obě z obou na `WebMessageFormat.Json` .  Chcete-li použít JSON, je nutné použít <xref:System.ServiceModel.WebHttpBinding> , který automaticky nakonfiguruje <xref:System.ServiceModel.Description.WebHttpBehavior> . Další informace o serializaci WCF naleznete v tématu [serializace a deserializace](serialization-and-deserialization.md). Další informace o JSON a WCF najdete v tématu [Service Station – Úvod k RESTful službám pomocí WCF](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).  
  
> [!IMPORTANT]
> Použití formátu JSON vyžaduje použití <xref:System.ServiceModel.WebHttpBinding> a, <xref:System.ServiceModel.Description.WebHttpBehavior> které nepodporují komunikaci SOAP. Služby, které komunikují s nástrojem, <xref:System.ServiceModel.WebHttpBinding> nepodporují vystavování metadat služby, takže nebudete moct k vygenerování proxy na straně klienta používat funkce Přidat odkaz na službu sady Visual Studio ani nástroj příkazového řádku Svcutil. Další informace o tom, jak programově volat služby, které používají <xref:System.ServiceModel.WebHttpBinding> , najdete v tématu [jak spotřebovávat služby REST pomocí WCF](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).  
  
## <a name="untyped-message-programming"></a>Programování netypové zprávy  
 Při práci přímo s netypovými objekty zpráv je nutné explicitně nastavit vlastnosti v netypové zprávě pro její serializaci jako JSON. Následující fragment kódu ukazuje, jak to provést.  
  
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

- [Integrace jazyka AJAX a podpora JSON](ajax-integration-and-json-support.md)
- [Samostatná serializace JSON](stand-alone-json-serialization.md)
- [Serializace JSON](../samples/json-serialization.md)
