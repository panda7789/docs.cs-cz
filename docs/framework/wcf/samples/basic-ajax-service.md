---
title: Základní služba AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 0bb8a2b28ea87cb0c22126540f6cdab604ca5120
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805977"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="2c486-102">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="2c486-102">Basic AJAX Service</span></span>
<span data-ttu-id="2c486-103">Tento příklad znázorňuje, jak vytvořit základní služby ASP.NET asynchronní JavaScript a XML (AJAX) (služba, která můžete přistupovat pomocí kódu jazyka JavaScript z webového prohlížeče klienta) pomocí služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2c486-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="2c486-104">Služba používá <xref:System.ServiceModel.Web.WebGetAttribute> atribut zajistit, že je služba reaguje na požadavky HTTP GET a je nakonfigurovaný na použití formát JavaScript Object Notation (JSON) dat pro odpovědi.</span><span class="sxs-lookup"><span data-stu-id="2c486-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>  
  
 <span data-ttu-id="2c486-105">Podpora jazyka AJAX v WCF je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX `ScriptManager` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2c486-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="2c486-106">Příklad WCF pomocí prvku ASP.NET AJAX, najdete v článku [AJAX ukázky](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="2c486-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c486-107">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2c486-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2c486-108">V následujícím kódu <xref:System.ServiceModel.Web.WebGetAttribute> je použit atribut `Add` operace zajistit, že služba reaguje na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="2c486-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="2c486-109">Kód používá GET pro jednoduchost (můžete vytvořit požadavek HTTP GET z libovolného webového prohlížeče).</span><span class="sxs-lookup"><span data-stu-id="2c486-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="2c486-110">GET můžete taky povolit ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2c486-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="2c486-111">Chybí výchozí hodnota je HTTP POST `WebGetAttribute` atribut.</span><span class="sxs-lookup"><span data-stu-id="2c486-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 <span data-ttu-id="2c486-112">Ukázkový soubor .svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, který přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> standardní koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="2c486-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="2c486-113">Koncový bod je nakonfigurován na prázdnou adresu relativně k souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="2c486-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="2c486-114">To znamená, že adresa služby je http://localhost/ServiceModelSamples/service.svc, s žádné další přípony jiný než název operace.</span><span class="sxs-lookup"><span data-stu-id="2c486-114">This means that the address of the service is http://localhost/ServiceModelSamples/service.svc, with no additional suffixes other than the operation name.</span></span>  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <span data-ttu-id="2c486-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> Je předem nakonfigurovaný zpřístupnit službu z klienta stránku ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="2c486-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="2c486-116">V následující části v souboru Web.config lze provést další změny konfigurace ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="2c486-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="2c486-117">Může být odebrán, pokud nejsou vyžadovány žádné další změny.</span><span class="sxs-lookup"><span data-stu-id="2c486-117">It can be removed if no extra changes are required.</span></span>  
  
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
  
 <span data-ttu-id="2c486-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> Nastaví výchozí formát dat pro službu do formátu JSON místo XML.</span><span class="sxs-lookup"><span data-stu-id="2c486-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="2c486-119">Chcete-li vyvolat službu, přejděte na http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 po dokončení sadu nahoru a vytvářet kroky uvidíte později v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="2c486-119">To invoke the service, navigate to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="2c486-120">Tato funkce testování je povolit pomocí služby požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="2c486-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>  
  
 <span data-ttu-id="2c486-121">Klient SimpleAjaxClientPage.aspx webová stránka obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na jednu operaci tlačítek na stránce.</span><span class="sxs-lookup"><span data-stu-id="2c486-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="2c486-122">`ScriptManager` Řízení se používá k zajištění proxy službě přístupné prostřednictvím jazyka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="2c486-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 <span data-ttu-id="2c486-123">Vytvoření instance místní proxy server a operace jsou vyvolány pomocí následujícího kódu JavaScript.</span><span class="sxs-lookup"><span data-stu-id="2c486-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 <span data-ttu-id="2c486-124">Pokud je úspěšné volání služby, vyvolá kód `onSuccess` obslužnou rutinu a výsledek operace se zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="2c486-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  <span data-ttu-id="2c486-125">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="2c486-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2c486-126">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2c486-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2c486-127">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2c486-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c486-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2c486-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="2c486-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c486-129">See Also</span></span>
