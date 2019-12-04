---
title: Ukázka služby AJAX s protokoly JSON a XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: ca9bdbfa135ac7dc0b69589d4f8fce07bc4c4afe
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716218"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="1a907-102">Ukázka služby AJAX s protokoly JSON a XML</span><span class="sxs-lookup"><span data-stu-id="1a907-102">AJAX Service with JSON and XML Sample</span></span>

<span data-ttu-id="1a907-103">Tento příklad ukazuje, jak použít Windows Communication Foundation (WCF) k vytvoření asynchronní služby JavaScriptu a XML (AJAX), která vrací buď JavaScript Object Notation (JSON) nebo XML data.</span><span class="sxs-lookup"><span data-stu-id="1a907-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="1a907-104">Ke službě AJAX můžete přistupovat pomocí kódu jazyka JavaScript z klienta webového prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="1a907-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="1a907-105">Tato ukázka sestaví na [základní ukázce služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="1a907-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="1a907-106">Na rozdíl od ostatních ukázek AJAX Tato ukázka nepoužívá ASP.NET AJAX a ovládací prvek <xref:System.Web.UI.ScriptManager>.</span><span class="sxs-lookup"><span data-stu-id="1a907-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="1a907-107">V případě některých dalších konfigurací je k dispozici služba WCF AJAX z jakékoli stránky HTML prostřednictvím JavaScriptu a tento scénář je zobrazen zde.</span><span class="sxs-lookup"><span data-stu-id="1a907-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="1a907-108">Příklad použití WCF s ASP.NET AJAX naleznete v tématu [ukázky AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="1a907-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>

<span data-ttu-id="1a907-109">Tato ukázka ukazuje, jak přepnout typ odezvy operace mezi JSON a XML.</span><span class="sxs-lookup"><span data-stu-id="1a907-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="1a907-110">Tato funkce je k dispozici bez ohledu na to, zda je služba nakonfigurována tak, aby k ní měl přístup ASP.NET AJAX nebo stránka klienta HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="1a907-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>

> [!NOTE]
> <span data-ttu-id="1a907-111">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="1a907-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="1a907-112">Chcete-li povolit použití klientů non-ASP.NET AJAX, použijte <xref:System.ServiceModel.Activation.WebServiceHostFactory> (není <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) v souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="1a907-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="1a907-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> přidá ke službě koncový bod <xref:System.ServiceModel.Description.WebHttpEndpoint> Standard.</span><span class="sxs-lookup"><span data-stu-id="1a907-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="1a907-114">Koncový bod je nakonfigurovaný na prázdné adrese relativní vzhledem k souboru. svc; To znamená, že adresa služby je `http://localhost/ServiceModelSamples/service.svc`, bez dalších přípon, než je název operace.</span><span class="sxs-lookup"><span data-stu-id="1a907-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

<span data-ttu-id="1a907-115">Následující oddíl v souboru Web. config lze použít k provedení dalších změn konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1a907-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="1a907-116">Je možné ji odebrat, pokud nejsou potřeba žádné další změny.</span><span class="sxs-lookup"><span data-stu-id="1a907-116">It can be removed if no extra changes are needed.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name="" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="1a907-117">Výchozí formát dat pro <xref:System.ServiceModel.Description.WebHttpEndpoint> je XML, zatímco výchozí formát dat pro <xref:System.ServiceModel.Description.WebScriptEndpoint> je JSON.</span><span class="sxs-lookup"><span data-stu-id="1a907-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="1a907-118">Další informace najdete v tématu [vytváření služeb WCF AJAX bez ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="1a907-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>

<span data-ttu-id="1a907-119">Služba v následující ukázce je standardní služba WCF se dvěma operacemi.</span><span class="sxs-lookup"><span data-stu-id="1a907-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="1a907-120">Obě operace vyžadují <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> styl těla u atributů <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute>, které jsou specifické pro `webHttp` chování a které nemají žádný vliv na přepínač formátu dat JSON nebo XML.</span><span class="sxs-lookup"><span data-stu-id="1a907-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

<span data-ttu-id="1a907-121">Formát odpovědi pro operaci je zadán jako XML, což je výchozí nastavení pro\<chování technologie [WebHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) .</span><span class="sxs-lookup"><span data-stu-id="1a907-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="1a907-122">Je však vhodné explicitně zadat formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1a907-122">However, it is good practice explicitly specify the response format.</span></span>

<span data-ttu-id="1a907-123">Druhá operace používá atribut `WebInvokeAttribute` a explicitně určuje JSON místo XML pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="1a907-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

<span data-ttu-id="1a907-124">Všimněte si, že v obou případech operace vrátí komplexní typ, `MathResult`, což je standardní typ kontraktu dat WCF.</span><span class="sxs-lookup"><span data-stu-id="1a907-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>

<span data-ttu-id="1a907-125">Webová stránka klienta XmlAjaxClientPage. htm obsahuje kód JavaScriptu, který vyvolá jednu z předchozích dvou operací, když uživatel klikne na stránce **provést výpočet (návratový kód JSON)** nebo **provést výpočet (vrácení XML)** .</span><span class="sxs-lookup"><span data-stu-id="1a907-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="1a907-126">Kód pro vyvolání služby vytvoří tělo JSON a odešle ho pomocí HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="1a907-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="1a907-127">Požadavek se v JavaScriptu vytvoří ručně, na rozdíl od ukázky [základní služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) a dalších ukázek pomocí ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="1a907-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>

```csharp
// Create HTTP request
var xmlHttp;
// Request instantiation code omitted…
// Result handler code omitted…

// Build the operation URL
var url = "service.svc/ajaxEndpoint/";
url = url + operation;

// Build the body of the JSON message
var body = '{"n1":';
body = body + document.getElementById("num1").value + ',"n2":';
body = body + document.getElementById("num2").value + '}';

// Send the HTTP request
xmlHttp.open("POST", url, true);
xmlHttp.setRequestHeader("Content-type", "application/json");
xmlHttp.send(body);
```

<span data-ttu-id="1a907-128">Když služba odpoví, zobrazí se odpověď bez dalšího zpracování v textovém poli na stránce.</span><span class="sxs-lookup"><span data-stu-id="1a907-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="1a907-129">To je implementováno pro demonstrační účely, které vám umožní přímo sledovat použité formáty dat XML a JSON.</span><span class="sxs-lookup"><span data-stu-id="1a907-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> <span data-ttu-id="1a907-130">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="1a907-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1a907-131">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="1a907-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1a907-132">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="1a907-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a907-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1a907-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1a907-134">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="1a907-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="1a907-135">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a907-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1a907-136">Sestavte řešení XmlAjaxService. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1a907-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="1a907-137">Přejděte na `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (neotevírejte XmlAjaxClientPage. htm v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="1a907-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a907-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a907-138">See also</span></span>

- [<span data-ttu-id="1a907-139">Služba AJAX využívající HTTP POST</span><span class="sxs-lookup"><span data-stu-id="1a907-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
