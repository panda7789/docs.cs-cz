---
title: Formátování protokolu HTTP na webu WCF
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: b6c9728fe40e26977366b73337e72b1514a12a19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184195"
---
# <a name="wcf-web-http-formatting"></a>Formátování protokolu HTTP na webu WCF
Programovací model WCF Web HTTP umožňuje dynamicky určit nejlepší formát pro operaci služby vrátit jeho odpověď. Jsou podporovány dvě metody pro určení vhodného formátu: automatické a explicitní.  
  
## <a name="automatic-formatting"></a>Automatické formátování  
 Pokud je povoleno, automatické formátování zvolí nejlepší formát, ve kterém se odpověď vrátí. Určuje nejlepší formát kontrolou následujícího, v pořadí:  
  
1. Typy médií v záhlaví Přijmout zprávy požadavku.  
  
2. Typ obsahu zprávy požadavku.  
  
3. Výchozí nastavení formátu v operaci.  
  
4. Výchozí nastavení formátu v webuHttpBehavior.  
  
 Pokud zpráva požadavku obsahuje hlavičku Přijmout, infrastruktura WCF (Windows Communication Foundation) vyhledá typ, který podporuje. Pokud `Accept` záhlaví určuje priority pro své typy médií, jsou dodrženy. Pokud v `Accept` záhlaví není nalezen žádný vhodný formát, použije se typ obsahu zprávy požadavku. Pokud není zadán žádný vhodný typ obsahu, použije se výchozí nastavení formátu pro operaci. Výchozí formát je nastaven `ResponseFormat` s <xref:System.ServiceModel.Web.WebGetAttribute> parametrem a <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy. Pokud není v operaci zadán žádný výchozí <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> formát, použije se hodnota vlastnosti. Automatické formátování závisí na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> vlastnosti. Pokud je tato `true`vlastnost nastavena na , wcf infrastruktury určuje nejlepší formát použít. Automatický výběr formátu je ve výchozím nastavení zakázán z důvodu zpětné kompatibility. Automatický výběr formátu lze povolit programově nebo prostřednictvím konfigurace. Následující příklad ukazuje, jak povolit automatický výběr formátu v kódu.  
  
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
  
 Automatické formátování lze také povolit prostřednictvím konfigurace. <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> Vlastnost můžete nastavit přímo <xref:System.ServiceModel.Description.WebHttpBehavior> na nebo <xref:System.ServiceModel.Description.WebHttpEndpoint>pomocí . Následující příklad ukazuje, jak povolit automatický <xref:System.ServiceModel.Description.WebHttpBehavior>výběr formátu na .  
  
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
  
 Následující příklad ukazuje, jak povolit <xref:System.ServiceModel.Description.WebHttpEndpoint>automatický výběr formátu pomocí aplikace .  
  
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
 Jak název napovídá, v explicitní formátování vývojář určuje nejlepší formát pro použití v rámci kódu operace. Pokud je nejlepším formátem XML nebo <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> JSON, vývojář nastaví na jeden <xref:System.ServiceModel.Web.WebMessageFormat.Xml> nebo . <xref:System.ServiceModel.Web.WebMessageFormat.Json> Pokud <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnost není explicitně nastavena, použije se výchozí formát operace.  
  
 Následující příklad zkontroluje parametr řetězce dotazu formátu pro formát, který má být používán. Pokud byl zadán, nastaví formát operace <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>pomocí .  
  
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
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 Pokud potřebujete podporovat jiné formáty než XML nebo JSON, definujte <xref:System.ServiceModel.Channels.Message>operaci tak, aby měla návratový typ . V rámci kódu operace určete vhodný formát, <xref:System.ServiceModel.Channels.Message> který chcete použít, a pak vytvořte objekt pomocí jedné z následujících metod:  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 Každá z těchto metod přebírá obsah a vytvoří zprávu s příslušným formátem. Metodu `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` lze použít k získání seznamu formátů preferovaných klientem v pořadí podle klesajících preferencí. Následující příklad ukazuje, `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` jak použít k určení formátu, který chcete použít, a potom použije příslušnou metodu create response k vytvoření zprávy odpovědi.  
  
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

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [UriTemplate a UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [Programovací objektový model WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
