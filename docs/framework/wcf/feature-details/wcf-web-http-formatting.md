---
title: "Formátování WCF Web HTTP"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3a41c6c7304234535993d83329c4faa464218e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="35d28-102">Formátování WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="35d28-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="35d28-103">Programovací model WCF Web HTTP umožňuje dynamicky určí nejlepší formát pro operaci služby vrátit v odpovědi.</span><span class="sxs-lookup"><span data-stu-id="35d28-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="35d28-104">Jsou podporovány dvě metody pro zjištění odpovídající formátu: automatické a explicitní.</span><span class="sxs-lookup"><span data-stu-id="35d28-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="35d28-105">Automatické formátování</span><span class="sxs-lookup"><span data-stu-id="35d28-105">Automatic formatting</span></span>  
 <span data-ttu-id="35d28-106">Když je povolené, automatického formátování vybere nejlepší formát k vrácení odpovědi.</span><span class="sxs-lookup"><span data-stu-id="35d28-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="35d28-107">Určuje doporučené formát kontrolou následujících v pořadí:</span><span class="sxs-lookup"><span data-stu-id="35d28-107">It determines the best format by checking the following, in order:</span></span>  
  
1.  <span data-ttu-id="35d28-108">Typy médií v hlavičce Accept zprávu požadavku.</span><span class="sxs-lookup"><span data-stu-id="35d28-108">The media types in the request message’s Accept header.</span></span>  
  
2.  <span data-ttu-id="35d28-109">Typ obsahu zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="35d28-109">The content-type of the request message.</span></span>  
  
3.  <span data-ttu-id="35d28-110">Výchozí formát nastavení v operaci.</span><span class="sxs-lookup"><span data-stu-id="35d28-110">The default format setting in the operation.</span></span>  
  
4.  <span data-ttu-id="35d28-111">Výchozí formát nastavení v WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="35d28-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="35d28-112">Pokud zpráva žádosti obsahuje hlavičku Accept [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hledání infrastruktury pro typ, který podporuje.</span><span class="sxs-lookup"><span data-stu-id="35d28-112">If the request message contains an Accept header the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="35d28-113">Pokud `Accept` záhlaví určuje priority pro jeho typy médií, jsou přijmout.</span><span class="sxs-lookup"><span data-stu-id="35d28-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="35d28-114">Pokud je nalezen žádný vhodný formát v `Accept` záhlaví, hlavičku content-type zprávy požadavku se používá.</span><span class="sxs-lookup"><span data-stu-id="35d28-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="35d28-115">Pokud není zadaný žádný vhodný typ obsahu, se používá formát výchozí nastavení pro operaci.</span><span class="sxs-lookup"><span data-stu-id="35d28-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="35d28-116">Výchozí formát nastavena `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="35d28-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="35d28-117">Pokud je zadán žádný výchozí formát operace, hodnota <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> vlastnost se používá.</span><span class="sxs-lookup"><span data-stu-id="35d28-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="35d28-118">Automatické formátování spoléhá na <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="35d28-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="35d28-119">Pokud je tato vlastnost nastavená na `true`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury určuje nejvhodnější používat.</span><span class="sxs-lookup"><span data-stu-id="35d28-119">When this property is set to `true`, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure determines the best format to use.</span></span> <span data-ttu-id="35d28-120">Automatický výběr formátu ve výchozím nastavení vypnutá pro zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="35d28-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="35d28-121">Automatický výběr formátu lze povolit prostřednictvím kódu programu, nebo prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="35d28-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="35d28-122">Následující příklad ukazuje, jak povolit automatický výběr formátu v kódu.</span><span class="sxs-lookup"><span data-stu-id="35d28-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
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
  
 <span data-ttu-id="35d28-123">Automatické formátování lze povolit také pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="35d28-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="35d28-124">Můžete nastavit <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> vlastnost přímo na <xref:System.ServiceModel.Description.WebHttpBehavior> nebo pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="35d28-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="35d28-125">Následující příklad ukazuje, jak povolit automatické formátovat výběr na <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="35d28-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
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
  
 <span data-ttu-id="35d28-126">Následující příklad ukazuje, jak povolit automatické formát výběru pomocí <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="35d28-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
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
  
## <a name="explicit-formatting"></a><span data-ttu-id="35d28-127">Explicitní formátování</span><span class="sxs-lookup"><span data-stu-id="35d28-127">Explicit formatting</span></span>  
 <span data-ttu-id="35d28-128">Jak již název napovídá, určuje vývojář při formátování explicitní nejlepší formát pro použití v rámci kód operace.</span><span class="sxs-lookup"><span data-stu-id="35d28-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="35d28-129">Pokud je nejlepší formátu XML nebo JSON vývojář nastaví <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> buď <xref:System.ServiceModel.Web.WebMessageFormat.Xml> nebo <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="35d28-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="35d28-130">Pokud <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> není explicitně nastavena vlastnost a potom se používá výchozí formát operace.</span><span class="sxs-lookup"><span data-stu-id="35d28-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="35d28-131">Následující příklad zkontroluje formát parametru řetězce dotazu pro formát, který se použije.</span><span class="sxs-lookup"><span data-stu-id="35d28-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="35d28-132">Pokud byla zadána, nastaví operace naformátovat pomocí <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span><span class="sxs-lookup"><span data-stu-id="35d28-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
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
  
 <span data-ttu-id="35d28-133">Pokud potřebujete pro podporu formátů než XML nebo JSON, definovat operaci tak, aby měl návratovým typem <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="35d28-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="35d28-134">V rámci kód operace určit příslušný formát použít, a potom vytvořit <xref:System.ServiceModel.Channels.Message> objektu pomocí jedné z následujících metod:</span><span class="sxs-lookup"><span data-stu-id="35d28-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="35d28-135">Každá z těchto metod trvá obsahu a vytvoří zprávu v příslušném formátu.</span><span class="sxs-lookup"><span data-stu-id="35d28-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="35d28-136">`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` Metoda slouží k získání seznamu formátů upřednostňovaný klientem v pořadí podle preference snížení.</span><span class="sxs-lookup"><span data-stu-id="35d28-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="35d28-137">Následující příklad ukazuje, jak používat `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` určit formát, který se používá a pak používá odpovídající vytvořit odpověď metodu pro vytvoření zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="35d28-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="35d28-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="35d28-138">See also</span></span>  
 <xref:System.UriTemplate>  
 <xref:System.UriTemplateMatch>  
 [<span data-ttu-id="35d28-139">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="35d28-139">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="35d28-140">UriTemplate a UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="35d28-140">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [<span data-ttu-id="35d28-141">Přehled modelu programování WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="35d28-141">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [<span data-ttu-id="35d28-142">Programovací objektový Model WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="35d28-142">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
