---
title: Základní služba AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 334cc9e53d7d9746c204abe37e7c30d00baa824b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716123"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="8403f-102">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="8403f-102">Basic AJAX Service</span></span>

<span data-ttu-id="8403f-103">Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření základní služby JavaScriptu (ASP.NET Asynchronous JavaScript and XML) (služba, ke které máte přístup pomocí kódu jazyka JavaScript z klienta webového prohlížeče).</span><span class="sxs-lookup"><span data-stu-id="8403f-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="8403f-104">Služba používá atribut <xref:System.ServiceModel.Web.WebGetAttribute> k zajištění toho, že služba reaguje na požadavky HTTP GET a je nakonfigurována tak, aby pro odpovědi používala formát dat JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="8403f-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>

<span data-ttu-id="8403f-105">Podpora AJAX ve WCF je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku `ScriptManager`.</span><span class="sxs-lookup"><span data-stu-id="8403f-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="8403f-106">Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="8403f-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8403f-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8403f-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="8403f-108">V následujícím kódu je <xref:System.ServiceModel.Web.WebGetAttribute> atribut použit na operaci `Add`, aby se zajistilo, že služba reaguje na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="8403f-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="8403f-109">Kód používá GET pro jednoduchost (požadavek HTTP GET můžete vytvořit z libovolného webového prohlížeče).</span><span class="sxs-lookup"><span data-stu-id="8403f-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="8403f-110">Můžete také použít GET a povolit ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8403f-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="8403f-111">HTTP POST je výchozí při absenci atributu `WebGetAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8403f-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="8403f-112">Ukázkový soubor. svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, který do služby přidá koncový bod <xref:System.ServiceModel.Description.WebScriptEndpoint> Standard.</span><span class="sxs-lookup"><span data-stu-id="8403f-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="8403f-113">Koncový bod je nakonfigurovaný na prázdné adrese relativní vzhledem k souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="8403f-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="8403f-114">To znamená, že adresa služby je `http://localhost/ServiceModelSamples/service.svc`, bez dalších přípon, než je název operace.</span><span class="sxs-lookup"><span data-stu-id="8403f-114">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>`

<span data-ttu-id="8403f-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> je předem nakonfigurovaný tak, aby služba byla přístupná z klientské stránky AJAX pro ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8403f-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="8403f-116">Následující oddíl v souboru Web. config lze použít k provedení dalších změn konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8403f-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="8403f-117">Tuto možnost lze odebrat, pokud nejsou vyžadovány žádné další změny.</span><span class="sxs-lookup"><span data-stu-id="8403f-117">It can be removed if no extra changes are required.</span></span>

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

<span data-ttu-id="8403f-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> nastaví výchozí formát dat pro službu na JSON namísto XML.</span><span class="sxs-lookup"><span data-stu-id="8403f-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="8403f-119">Chcete-li vyvolat službu, přejděte na `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` po dokončení kroků nastavení a sestavení, které jsou uvedeny dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8403f-119">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="8403f-120">Tato funkce testování je povolena pomocí požadavku HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="8403f-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>

<span data-ttu-id="8403f-121">Klientská webová stránka SimpleAjaxClientPage. aspx obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na stránku s jedním z těchto tlačítek operace.</span><span class="sxs-lookup"><span data-stu-id="8403f-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="8403f-122">`ScriptManager` ovládací prvek slouží k vytvoření proxy serveru pro přístup k službě prostřednictvím JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="8403f-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">
    <Services>
        <asp:ServiceReference Path="service.svc" />
    </Services>
</asp:ScriptManager>
```

<span data-ttu-id="8403f-123">Instance místního proxy serveru a operace jsou vyvolány pomocí následujícího kódu JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="8403f-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>

```javascript
// Code for extracting arguments n1 and n2 omitted…
// Instantiate a service proxy
var proxy = new SimpleAjaxService.ICalculator();
// Code for selecting operation omitted…
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);
```

<span data-ttu-id="8403f-124">Pokud je volání služby úspěšné, kód vyvolá obslužnou rutinu `onSuccess` a výsledek operace se zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="8403f-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("result").value = mathResult;
}
```

> [!IMPORTANT]
> <span data-ttu-id="8403f-125">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="8403f-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8403f-126">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="8403f-126">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8403f-127">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="8403f-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8403f-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8403f-128">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
