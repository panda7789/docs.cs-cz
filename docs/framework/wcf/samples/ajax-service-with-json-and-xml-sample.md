---
title: Ukázka služby AJAX s protokoly JSON a XML
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: e5f2838575b212f6b95fd01b469d771017ef534c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207475"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="9931b-102">Ukázka služby AJAX s protokoly JSON a XML</span><span class="sxs-lookup"><span data-stu-id="9931b-102">AJAX Service with JSON and XML Sample</span></span>
<span data-ttu-id="9931b-103">Tento příklad ukazuje, jak použít Windows Communication Foundation (WCF) k vytvoření služby asynchronní JavaScript a XML (AJAX), který vrací data JavaScript Object Notation (JSON) nebo XML.</span><span class="sxs-lookup"><span data-stu-id="9931b-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="9931b-104">Služby AJAX můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta.</span><span class="sxs-lookup"><span data-stu-id="9931b-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="9931b-105">Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="9931b-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="9931b-106">Na rozdíl od ostatních AJAX vzorků, tato ukázka nepoužívá technologie ASP.NET AJAX a <xref:System.Web.UI.ScriptManager> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9931b-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="9931b-107">Některé další konfigurace služeb WCF AJAX je přístupný z jakékoli stránky HTML pomocí JavaScriptu a tento scénář je znázorněna zde.</span><span class="sxs-lookup"><span data-stu-id="9931b-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="9931b-108">Příklad použití WCF pomocí ASP.NET AJAX, naleznete v tématu [AJAX ukázky](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="9931b-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>
  
 <span data-ttu-id="9931b-109">Tento příklad ukazuje, jak přepnout typ odpovědi z operace mezi JSON a XML.</span><span class="sxs-lookup"><span data-stu-id="9931b-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="9931b-110">Tato funkce je dostupná bez ohledu na to, zda je služba nakonfigurována přistupovat pomocí technologie ASP.NET AJAX nebo stránku HTML/JavaScript klienta.</span><span class="sxs-lookup"><span data-stu-id="9931b-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9931b-111">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9931b-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>
  
<span data-ttu-id="9931b-112">Chcete-li povolit používání technologie ASP.NET AJAX klientů, použijte <xref:System.ServiceModel.Activation.WebServiceHostFactory> (ne <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) v souboru SVC.</span><span class="sxs-lookup"><span data-stu-id="9931b-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <xref:System.ServiceModel.Activation.WebServiceHostFactory> <span data-ttu-id="9931b-113">Přidá <xref:System.ServiceModel.Description.WebHttpEndpoint> standardní koncový bod ke službě.</span><span class="sxs-lookup"><span data-stu-id="9931b-113">adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="9931b-114">Koncový bod je nakonfigurována na prázdnou adresu relativní k souboru .svc; To znamená, že je adresa služby `http://localhost/ServiceModelSamples/service.svc`, se žádné další přípony jiný než název operace.</span><span class="sxs-lookup"><span data-stu-id="9931b-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 <span data-ttu-id="9931b-115">Následující části v souboru Web.config je možné provést další změny konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9931b-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="9931b-116">Je možné odebrat, pokud nejsou potřeba žádné další změny.</span><span class="sxs-lookup"><span data-stu-id="9931b-116">It can be removed if no extra changes are needed.</span></span>  
  
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
  
 <span data-ttu-id="9931b-117">Data výchozí formát pro <xref:System.ServiceModel.Description.WebHttpEndpoint> XML, se při výchozí formát dat pro <xref:System.ServiceModel.Description.WebScriptEndpoint> je JSON.</span><span class="sxs-lookup"><span data-stu-id="9931b-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="9931b-118">Další informace najdete v tématu [vytváření služeb WCF AJAX bez ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="9931b-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>  
  
 <span data-ttu-id="9931b-119">Tato služba v následujícím příkladu je standardní služby WCF s dvě operace.</span><span class="sxs-lookup"><span data-stu-id="9931b-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="9931b-120">Obě operace vyžadují <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> textu ve stylu <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy, které jsou specifické pro `webHttp` chování a nemá žádný vliv na přepínač formátu dat JSON a XML.</span><span class="sxs-lookup"><span data-stu-id="9931b-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```

 <span data-ttu-id="9931b-121">Formát odpovědi pro operaci je zadán jako XML, což je výchozí nastavení [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) chování.</span><span class="sxs-lookup"><span data-stu-id="9931b-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="9931b-122">Ale je dobrým zvykem explicitně určit formát odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9931b-122">However, it is good practice explicitly specify the response format.</span></span>  
  
 <span data-ttu-id="9931b-123">Operace použije `WebInvokeAttribute` atribut a explicitně určí JSON místo XML pro odpověď.</span><span class="sxs-lookup"><span data-stu-id="9931b-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>  

```csharp
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```

 <span data-ttu-id="9931b-124">Všimněte si, že v obou případech operace vrátí komplexní typ, `MathResult`, což je standardní typ kontraktu dat WCF.</span><span class="sxs-lookup"><span data-stu-id="9931b-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>  
  
 <span data-ttu-id="9931b-125">Klient XmlAjaxClientPage.htm webová stránka obsahuje kód JavaScriptu, který vyvolá jednu z předchozí dvě operace, když uživatel klikne **provedení výpočtu (vrácený kód JSON)** nebo **provedení výpočtu (návratový XML)**  tlačítka na stránce.</span><span class="sxs-lookup"><span data-stu-id="9931b-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="9931b-126">Kód se vyvolat službu vytvoří text JSON a odešle ji pomocí HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="9931b-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="9931b-127">Žádost je ručně vytvořené v jazyce JavaScript, na rozdíl od [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázky a další ukázky pomocí prvku ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="9931b-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>  

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

 <span data-ttu-id="9931b-128">Pokud služba odpoví, bez dalšího zpracování v textovém poli na stránce zobrazí odpověď.</span><span class="sxs-lookup"><span data-stu-id="9931b-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="9931b-129">To je implementováno pro demonstrační účely můžete přímo sledovat formáty dat XML a JSON použít.</span><span class="sxs-lookup"><span data-stu-id="9931b-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>  

```javascript
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```

> [!IMPORTANT]
>  <span data-ttu-id="9931b-130">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="9931b-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9931b-131">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9931b-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9931b-132">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9931b-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9931b-133">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9931b-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9931b-134">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="9931b-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9931b-135">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9931b-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9931b-136">Sestavte řešení XmlAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9931b-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9931b-137">Přejděte na `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (neotevírejte XmlAjaxClientPage.htm v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="9931b-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9931b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9931b-138">See also</span></span>

- [<span data-ttu-id="9931b-139">Služba AJAX, která používá HTTP POST</span><span class="sxs-lookup"><span data-stu-id="9931b-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
