---
title: "Formátování WCF Web HTTP"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab18e739b061ac6d28877eaac23c258a79f07a2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-web-http-formatting"></a>Formátování WCF Web HTTP
Programovací model WCF Web HTTP umožňuje dynamicky určí nejlepší formát pro operaci služby vrátit v odpovědi. Jsou podporovány dvě metody pro zjištění odpovídající formátu: automatické a explicitní.  
  
## <a name="automatic-formatting"></a>Automatické formátování  
 Když je povolené, automatického formátování vybere nejlepší formát k vrácení odpovědi. Určuje doporučené formát kontrolou následujících v pořadí:  
  
1.  Typy médií v hlavičce Accept zprávu požadavku.  
  
2.  Typ obsahu zprávy požadavku.  
  
3.  Výchozí formát nastavení v operaci.  
  
4.  Výchozí formát nastavení v WebHttpBehavior.  
  
 Pokud zpráva žádosti obsahuje hlavičku Accept [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hledání infrastruktury pro typ, který podporuje. Pokud `Accept` záhlaví určuje priority pro jeho typy médií, jsou přijmout. Pokud je nalezen žádný vhodný formát v `Accept` záhlaví, hlavičku content-type zprávy požadavku se používá. Pokud není zadaný žádný vhodný typ obsahu, se používá formát výchozí nastavení pro operaci. Výchozí formát nastavena `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy. Pokud je zadán žádný výchozí formát operace, hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> vlastnost se používá. Automatické formátování spoléhá na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> vlastnost. Pokud je tato vlastnost nastavená na `true`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury určuje nejvhodnější používat. Automatický výběr formátu ve výchozím nastavení vypnutá pro zpětné kompatibility. Automatický výběr formátu lze povolit prostřednictvím kódu programu, nebo prostřednictvím konfigurace. Následující příklad ukazuje, jak povolit automatický výběr formátu v kódu.  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract     
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();        
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 Automatické formátování lze povolit také pomocí konfigurace. Můžete nastavit <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> vlastnost přímo na <xref:System.ServiceModel.Description.WebHttpBehavior> nebo pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint>. Následující příklad ukazuje, jak povolit automatické formátovat výběr na <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Následující příklad ukazuje, jak povolit automatické formát výběru pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint>.  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a>Explicitní formátování  
 Jak již název napovídá, určuje vývojář při formátování explicitní nejlepší formát pro použití v rámci kód operace. Pokud je nejlepší formátu XML nebo JSON vývojář nastaví <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> buď <xref:System.ServiceModel.Web.WebMessageFormat.Xml> nebo <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Pokud <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> není explicitně nastavena vlastnost a potom se používá výchozí formát operace.  
  
 Následující příklad zkontroluje formát parametru řetězce dotazu pro formát, který se použije. Pokud byla zadána, nastaví operace naformátovat pomocí <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
         // if a format query string parameter has been specified, set the response format to that. If no such  
         // query string parameter exists the Accept header will be used  
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
             if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
             {  
                  WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;  
             }  
             else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                 throw new WebFaultException<string>(string.Format("Unsupported format '{0}'", formatQueryStringValue), HttpStatusCode.BadRequest);  
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 Pokud potřebujete pro podporu formátů než XML nebo JSON, definovat operaci tak, aby měl návratovým typem <xref:System.ServiceModel.Channels.Message>. V rámci kód operace určit příslušný formát použít, a potom vytvořit <xref:System.ServiceModel.Channels.Message> objektu pomocí jedné z následujících metod:  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 Každá z těchto metod trvá obsahu a vytvoří zprávu v příslušném formátu. `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Metoda slouží k získání seznamu formátů upřednostňovaný klientem v pořadí podle preference snížení. Následující příklad ukazuje, jak používat `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` určit formát, který se používá a pak používá odpovídající vytvořit odpověď metodu pro vytvoření zprávu odpovědi.  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.UriTemplate>  
 <xref:System.UriTemplateMatch>  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [UriTemplate a UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [Programovací objektový model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
