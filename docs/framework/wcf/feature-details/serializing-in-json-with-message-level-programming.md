---
title: Serializace ve formátu Json s programováním na úrovni zpráv
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 9c5ad29e2ddbdde3ae560c4ff2af224bc3a71ad9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855698"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serializace ve formátu Json s programováním na úrovni zpráv
WCF podporuje serializaci dat ve formátu JSON. Toto téma popisuje, jak zjistit WCF k serializaci typů pomocí <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Zadanou zprávu programování  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Se používá při <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> se použije pro operaci služby. Obě tyto atributy umožňují určit `RequestFormat` a `ResponseFormat`. Chcete použít JSON pro požadavky a odpovědi nastavte oba z těchto `WebMessageFormat.Json`.  Chcete-li použít JSON je nutné použít <xref:System.ServiceModel.WebHttpBinding> který automaticky nakonfiguruje <xref:System.ServiceModel.Description.WebHttpBehavior>. Další informace o serializaci WCF najdete v tématu: [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [serializace ve službě Windows Communication Foundation](https://msdn.microsoft.com/magazine/cc163569.aspx). Další informace o JSON a WCF najdete v části [Úvod do služby RESTfull s použitím technologie WCF](https://msdn.microsoft.com/magazine/dd315413.aspx), [podporou JSON pro vytváření služeb WCF v rozhraní .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), a [přehled REST ve službě WCF](https://msdn.microsoft.com/netframework/dd547388).  
  
> [!IMPORTANT]
>  Pomocí formátu JSON, vyžaduje použití <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> který nepodporuje komunikaci protokolu SOAP. Služby, které komunikují <xref:System.ServiceModel.WebHttpBinding> nepodporují zpřístupňuje metadata služby, takže nebudete moci generovat proxy server na straně klienta pomocí funkce Přidat odkaz na službu sady Visual Studio nebo nástroj příkazového řádku svcutil. Další informace, jak můžete programově volat služby, které používají <xref:System.ServiceModel.WebHttpBinding>, naleznete v tématu [jak využívat služby REST s použitím technologie WCF](https://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## <a name="untyped-message-programming"></a>Programování bez typu zprávy  
 Při práci přímo s objekty netypové zpráv, musíte explicitně nastavit vlastnosti netypové zprávy ho serializovat jako JSON. Následující fragment kódu ukazuje, jak to provést.  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Viz také  
 [Integrace jazyka AJAX a podpora JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [Samostatná serializace JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [Serializace JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
