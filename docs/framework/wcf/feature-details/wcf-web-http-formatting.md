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
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="67dc5-102">Webové HTTP WCF – formátování</span><span class="sxs-lookup"><span data-stu-id="67dc5-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="67dc5-103">Model programování webových služeb HTTP WCF umožňuje dynamicky určit nejlepší formát pro operaci služby, která vrátí odpověď v.</span><span class="sxs-lookup"><span data-stu-id="67dc5-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="67dc5-104">Podporovány jsou dvě metody určení vhodného formátu: automatické a explicitní.</span><span class="sxs-lookup"><span data-stu-id="67dc5-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="67dc5-105">Automatické formátování</span><span class="sxs-lookup"><span data-stu-id="67dc5-105">Automatic formatting</span></span>  
 <span data-ttu-id="67dc5-106">Pokud je povoleno, automatické formátování zvolí nejlepší formát, ve kterém se má vrátit odpověď.</span><span class="sxs-lookup"><span data-stu-id="67dc5-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="67dc5-107">Určuje nejlepší formát kontrolou následujícího, v uvedeném pořadí:</span><span class="sxs-lookup"><span data-stu-id="67dc5-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="67dc5-108">Typy médií v hlavičce Accept zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="67dc5-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="67dc5-109">Typ obsahu zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="67dc5-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="67dc5-110">Výchozí nastavení formátu v operaci.</span><span class="sxs-lookup"><span data-stu-id="67dc5-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="67dc5-111">Výchozí nastavení formátu v WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="67dc5-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="67dc5-112">Pokud zpráva požadavku obsahuje hlavičku Accept, vyhledá infrastruktura Windows Communication Foundation (WCF) typ, který podporuje.</span><span class="sxs-lookup"><span data-stu-id="67dc5-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="67dc5-113">Pokud `Accept` Hlavička určuje priority pro své typy médií, budou přijaty.</span><span class="sxs-lookup"><span data-stu-id="67dc5-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="67dc5-114">Pokud se v hlavičce nenajde žádný vhodný formát `Accept` , použije se typ obsahu zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="67dc5-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="67dc5-115">Pokud není zadán vhodný typ obsahu, použije se výchozí nastavení formátu pro tuto operaci.</span><span class="sxs-lookup"><span data-stu-id="67dc5-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="67dc5-116">Výchozí formát je nastaven s použitím `ResponseFormat` parametru <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> atributů a.</span><span class="sxs-lookup"><span data-stu-id="67dc5-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="67dc5-117">Pokud pro operaci není zadán výchozí formát, <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> je použita hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="67dc5-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="67dc5-118">Automatické formátování spoléhá na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="67dc5-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="67dc5-119">Pokud je tato vlastnost nastavena na hodnotu `true` , infrastruktura WCF určí nejvhodnější formát, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="67dc5-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="67dc5-120">Automatický výběr formátu je ve výchozím nastavení zakázán pro účely zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="67dc5-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="67dc5-121">Automatický výběr formátu lze povolit prostřednictvím kódu programu nebo prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="67dc5-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="67dc5-122">Následující příklad ukazuje, jak povolit automatický výběr formátu v kódu.</span><span class="sxs-lookup"><span data-stu-id="67dc5-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
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
  
 <span data-ttu-id="67dc5-123">Automatické formátování lze také povolit prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="67dc5-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="67dc5-124">Vlastnost lze nastavit <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> přímo na <xref:System.ServiceModel.Description.WebHttpBehavior> nebo pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="67dc5-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="67dc5-125">Následující příklad ukazuje, jak povolit automatický výběr formátu v <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="67dc5-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
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
  
 <span data-ttu-id="67dc5-126">Následující příklad ukazuje, jak povolit automatický výběr formátu pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="67dc5-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
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
  
## <a name="explicit-formatting"></a><span data-ttu-id="67dc5-127">Explicitní formátování</span><span class="sxs-lookup"><span data-stu-id="67dc5-127">Explicit formatting</span></span>  
 <span data-ttu-id="67dc5-128">Jak název naznačuje, v explicitním formátování vývojář určí nejlepší formát pro použití v kódu operace.</span><span class="sxs-lookup"><span data-stu-id="67dc5-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="67dc5-129">Pokud je nejlepší formát XML nebo JSON, vývojář nastaví <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> buď <xref:System.ServiceModel.Web.WebMessageFormat.Xml> nebo <xref:System.ServiceModel.Web.WebMessageFormat.Json> .</span><span class="sxs-lookup"><span data-stu-id="67dc5-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="67dc5-130">Pokud <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> vlastnost není explicitně nastavená, použije se výchozí formát operace.</span><span class="sxs-lookup"><span data-stu-id="67dc5-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="67dc5-131">Následující příklad zkontroluje parametr řetězce formátu dotazu pro formát, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="67dc5-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="67dc5-132">Pokud byl zadán, nastaví formát operace pomocí <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> .</span><span class="sxs-lookup"><span data-stu-id="67dc5-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
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
  
 <span data-ttu-id="67dc5-133">Pokud potřebujete podporovat jiné formáty než XML nebo JSON, definujte operaci, aby měla návratový typ <xref:System.ServiceModel.Channels.Message> .</span><span class="sxs-lookup"><span data-stu-id="67dc5-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="67dc5-134">V rámci kódu operace určete příslušný formát, který se má použít, a pak vytvořte <xref:System.ServiceModel.Channels.Message> objekt pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="67dc5-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="67dc5-135">Každá z těchto metod vezme obsah a vytvoří zprávu s odpovídajícím formátem.</span><span class="sxs-lookup"><span data-stu-id="67dc5-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="67dc5-136">`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements`Metoda se dá použít k získání seznamu formátů preferovaných klientem v pořadí zmenšení priority.</span><span class="sxs-lookup"><span data-stu-id="67dc5-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="67dc5-137">Následující příklad ukazuje, jak použít `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` k určení používaného formátu a následnému vytvoření zprávy odpovědi pomocí vhodné metody Create Response.</span><span class="sxs-lookup"><span data-stu-id="67dc5-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67dc5-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="67dc5-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="67dc5-139">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="67dc5-139">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="67dc5-140">UriTemplate a UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="67dc5-140">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="67dc5-141">Přehled programovacího modelu webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="67dc5-141">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="67dc5-142">Programovací objektový model WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="67dc5-142">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
