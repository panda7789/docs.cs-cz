---
title: Webové HTTP WCF – formátování
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 011ff4f2e667268fac1aa2d82c0a2c4ffefc8dde
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585555"
---
# <a name="wcf-web-http-formatting"></a>Webové HTTP WCF – formátování
Model programování webových služeb HTTP WCF umožňuje dynamicky určit nejlepší formát pro operaci služby, která vrátí odpověď v. Podporovány jsou dvě metody určení vhodného formátu: automatické a explicitní.  
  
## <a name="automatic-formatting"></a>Automatické formátování  
 Pokud je povoleno, automatické formátování zvolí nejlepší formát, ve kterém se má vrátit odpověď. Určuje nejlepší formát kontrolou následujícího, v uvedeném pořadí:  
  
1. Typy médií v hlavičce Accept zprávy požadavku.  
  
2. Typ obsahu zprávy požadavku.  
  
3. Výchozí nastavení formátu v operaci.  
  
4. Výchozí nastavení formátu v WebHttpBehavior.  
  
 Pokud zpráva požadavku obsahuje hlavičku Accept, vyhledá infrastruktura Windows Communication Foundation (WCF) typ, který podporuje. Pokud `Accept` Hlavička určuje priority pro své typy médií, budou přijaty. Pokud se v hlavičce nenajde žádný vhodný formát `Accept` , použije se typ obsahu zprávy požadavku. Pokud není zadán vhodný typ obsahu, použije se výchozí nastavení formátu pro tuto operaci. Výchozí formát je nastaven s použitím `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> atributů a. Pokud pro operaci není zadán výchozí formát, <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> je použita hodnota vlastnosti. Automatické formátování spoléhá na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> vlastnost. Pokud je tato vlastnost nastavena na hodnotu `true` , infrastruktura WCF určí nejvhodnější formát, který se má použít. Automatický výběr formátu je ve výchozím nastavení zakázán pro účely zpětné kompatibility. Automatický výběr formátu lze povolit prostřednictvím kódu programu nebo prostřednictvím konfigurace. Následující příklad ukazuje, jak povolit automatický výběr formátu v kódu.  
  
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
  
 Automatické formátování lze také povolit prostřednictvím konfigurace. Vlastnost lze nastavit <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> přímo na <xref:System.ServiceModel.Description.WebHttpBehavior> nebo pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint> . Následující příklad ukazuje, jak povolit automatický výběr formátu v <xref:System.ServiceModel.Description.WebHttpBehavior> .  
  
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
  
 Následující příklad ukazuje, jak povolit automatický výběr formátu pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint> .  
  
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
 Jak název naznačuje, v explicitním formátování vývojář určí nejlepší formát pro použití v kódu operace. Pokud je nejlepší formát XML nebo JSON, vývojář nastaví <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> buď <xref:System.ServiceModel.Web.WebMessageFormat.Xml> nebo <xref:System.ServiceModel.Web.WebMessageFormat.Json> . Pokud <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnost není explicitně nastavená, použije se výchozí formát operace.  
  
 Následující příklad zkontroluje parametr řetězce formátu dotazu pro formát, který má být použit. Pokud byl zadán, nastaví formát operace pomocí <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> .  
  
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
  
 Pokud potřebujete podporovat jiné formáty než XML nebo JSON, definujte operaci, aby měla návratový typ <xref:System.ServiceModel.Channels.Message> . V rámci kódu operace určete příslušný formát, který se má použít, a pak vytvořte <xref:System.ServiceModel.Channels.Message> objekt pomocí jedné z následujících metod:  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 Každá z těchto metod vezme obsah a vytvoří zprávu s odpovídajícím formátem. `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements`Metoda se dá použít k získání seznamu formátů preferovaných klientem v pořadí zmenšení priority. Následující příklad ukazuje, jak použít `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` k určení používaného formátu a následnému vytvoření zprávy odpovědi pomocí vhodné metody Create Response.  
  
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
- [Programovací model webových služeb HTTP WCF](wcf-web-http-programming-model.md)
- [UriTemplate a UriTemplateTable](uritemplate-and-uritemplatetable.md)
- [Přehled programovacího modelu webových služeb HTTP WCF](wcf-web-http-programming-model-overview.md)
- [Programovací objektový model WCF Web HTTP](wcf-web-http-programming-object-model.md)
