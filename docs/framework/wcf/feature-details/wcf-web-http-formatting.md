---
title: Formátování WCF Web HTTP
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: f3d3a2d992f234c690f3fb87514b700a6596a5fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331036"
---
# <a name="wcf-web-http-formatting"></a>Formátování WCF Web HTTP
Model programování webových služeb HTTP WCF umožňuje dynamicky určovat nejlepší formát pro operaci služby vrátit v odpovědi. Dvě metody pro zjištění odpovídající formátu jsou podporovány: automatické a explicitní.  
  
## <a name="automatic-formatting"></a>Automatické formátování  
 Při povolení automatické formátování vybere nejlepší formát ke vrácení odpovědi. Určuje nejvhodnější formát kontrolou následujících akcí v pořadí:  
  
1. Typy médií v hlavičce Accept zprávy požadavku.  
  
2. Typ obsahu zprávy s požadavkem.  
  
3. Výchozí formát nastavení v operaci.  
  
4. Výchozí formát nastavení WebHttpBehavior.  
  
 Pokud zpráva žádosti obsahuje hlavičku Accept infrastrukturu Windows Communication Foundation (WCF) vyhledá pro typ, který podporuje. Pokud `Accept` hlavičky určuje priority pro jeho typy médií, jsou respektovat. Pokud se nenajde žádný vhodný formát v `Accept` hlavička content-type zprávy požadavku se používá. Pokud není zadán žádný vhodný typ obsahu, je používán formát výchozí nastavení pro tuto operaci. Výchozí formát nastavená `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy. Pokud žádná výchozí formát je uveden pro operaci, hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> vlastnost se používá. Automatické formátování se může spolehnout <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> vlastnost. Pokud je tato vlastnost nastavena na `true`, určuje nejvhodnější formát infrastruktura WCF. Automatický výběr formátu je zakázané ve výchozím nastavení pro zpětnou kompatibilitu. Automatický výběr formátu je možné povolit programově nebo prostřednictvím konfigurace. Následující příklad ukazuje, jak povolit automatický výběr formátu v kódu.  
  
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
  
 Automatické formátování je také možné povolit prostřednictvím konfigurace. Můžete nastavit <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> přímo na vlastnost <xref:System.ServiceModel.Description.WebHttpBehavior> nebo pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint>. Následující příklad ukazuje, jak povolit výběr automatického formátu na <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
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
  
 Následující příklad ukazuje, jak povolit výběr automatického formátu pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint>.  
  
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
 Jak již název napovídá, v explicitní formátování vývojáře určuje nejlepšího formátu pro použití v rámci operace kódu. Pokud je nejlepší formátu XML nebo JSON vývojář nastaví <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> buď <xref:System.ServiceModel.Web.WebMessageFormat.Xml> nebo <xref:System.ServiceModel.Web.WebMessageFormat.Json>. Pokud <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> není explicitně nastavena vlastnost a potom se používá výchozí formát operaci zopakovat.  
  
 Následující příklad ověří formát parametru řetězce dotazu pro formát určený. Pokud byl zadán, nastaví operace formátování pomocí <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.  
  
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
  
 Pokud budete potřebovat pro podporu formátů než XML nebo JSON, definovat operaci mít návratový typ <xref:System.ServiceModel.Channels.Message>. V rámci kód operace určit vhodný formát používat a pak vytvořte <xref:System.ServiceModel.Channels.Message> pomocí jedné z následujících metod:  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 Každá z těchto metod má obsahu a vytvoří zprávu v příslušném formátu. `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Metody slouží k získání seznamu formátů upřednostňované klientem v pořadí sestupný předvoleb. Následující příklad ukazuje, jak používat `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` k určení formátu pro použití a pak používá odpovídající vytvořit odpověď metodu pro vytvoření zprávy s odpovědí.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [UriTemplate a UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [Přehled programovacího modelu webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [Programovací objektový model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
