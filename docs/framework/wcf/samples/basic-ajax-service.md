---
title: Základní služba AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 8bcfb9a751670d3d1c32de6d8e6f7dc1b84ea30d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002700"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="8d864-102">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="8d864-102">Basic AJAX Service</span></span>
<span data-ttu-id="8d864-103">Tento příklad ukazuje, jak pomocí služby Windows Communication Foundation (WCF) základní asynchronní jazyka JavaScript technologie ASP.NET a XML (AJAX) službu (služba, která můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta).</span><span class="sxs-lookup"><span data-stu-id="8d864-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="8d864-104">Služba používá <xref:System.ServiceModel.Web.WebGetAttribute> atribut zajistíte, že služba reaguje na požadavky HTTP GET a je nakonfigurován na použití formátu dat JavaScript Object Notation (JSON) pro odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8d864-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>  
  
 <span data-ttu-id="8d864-105">Podpora pro AJAX ve službě WCF je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8d864-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="8d864-106">Příklad použití WCF pomocí ASP.NET AJAX, najdete v článku [AJAX ukázky](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="8d864-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d864-107">Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8d864-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8d864-108">V následujícím kódu <xref:System.ServiceModel.Web.WebGetAttribute> atributu se použije pro `Add` operace Ujistěte se, že služba reaguje na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="8d864-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="8d864-109">Tento kód použije GET pro zjednodušení (lze vytvořit požadavek HTTP GET z libovolného webového prohlížeče).</span><span class="sxs-lookup"><span data-stu-id="8d864-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="8d864-110">Také vám pomůže získat povolit ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8d864-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="8d864-111">Chybí výchozí hodnota je HTTP POST `WebGetAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="8d864-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 <span data-ttu-id="8d864-112">Používá ukázkový soubor SVC <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, který přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> standardní koncový bod ke službě.</span><span class="sxs-lookup"><span data-stu-id="8d864-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="8d864-113">Koncový bod je nakonfigurována na prázdnou adresu vzhledem k souboru SVC.</span><span class="sxs-lookup"><span data-stu-id="8d864-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="8d864-114">To znamená, že je adresa služby `http://localhost/ServiceModelSamples/service.svc`, se žádné další přípony jiný než název operace.</span><span class="sxs-lookup"><span data-stu-id="8d864-114">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <span data-ttu-id="8d864-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> Je předem nakonfigurovaný k zpřístupnění služby ze stránky technologie ASP.NET AJAX klienta.</span><span class="sxs-lookup"><span data-stu-id="8d864-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="8d864-116">Následující části v souboru Web.config je možné provést další změny konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8d864-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="8d864-117">Je možné odebrat, pokud nejsou potřeba žádné další změny.</span><span class="sxs-lookup"><span data-stu-id="8d864-117">It can be removed if no extra changes are required.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name=""  />  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="8d864-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> Nastaví výchozí formát dat pro službu do formátu JSON místo XML.</span><span class="sxs-lookup"><span data-stu-id="8d864-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="8d864-119">Abyste mohli vyvolat službu, přejděte na `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` po dokončení sady si a sestavte kroky uvedené dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8d864-119">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="8d864-120">Tato funkce testování se povoluje pomocí požadavku HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="8d864-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>  
  
 <span data-ttu-id="8d864-121">Klient SimpleAjaxClientPage.aspx webová stránka obsahuje kód technologie ASP.NET se vyvolat službu pokaždé, když uživatel klikne jedno z tlačítek operace na stránce.</span><span class="sxs-lookup"><span data-stu-id="8d864-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="8d864-122">`ScriptManager` Ovládací prvek se používá aby proxy pro službu pomocí JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="8d864-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 <span data-ttu-id="8d864-123">Místní proxy server je vytvořena instance a operace jsou vyvolány pomocí následujícího kódu jazyka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="8d864-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 <span data-ttu-id="8d864-124">Pokud je volání služby úspěšná, kód vyvolá `onSuccess` obslužnou rutinu a výsledek operace se zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="8d864-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  <span data-ttu-id="8d864-125">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="8d864-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8d864-126">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8d864-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8d864-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8d864-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8d864-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8d864-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
