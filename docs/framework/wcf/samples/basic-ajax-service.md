---
title: Základní služba AJAX
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 2d3770630df693093b05868f00c409f8245f858b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925241"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="0537a-102">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="0537a-102">Basic AJAX Service</span></span>
<span data-ttu-id="0537a-103">Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření základní služby JavaScriptu (ASP.NET Asynchronous JavaScript and XML) (služba, ke které máte přístup pomocí kódu jazyka JavaScript z klienta webového prohlížeče).</span><span class="sxs-lookup"><span data-stu-id="0537a-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="0537a-104">Služba používá <xref:System.ServiceModel.Web.WebGetAttribute> atribut k zajištění toho, že služba reaguje na požadavky HTTP GET a je nakonfigurována tak, aby pro odpovědi používala formát dat JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="0537a-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>  
  
 <span data-ttu-id="0537a-105">Podpora AJAX ve WCF je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0537a-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="0537a-106">Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="0537a-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0537a-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0537a-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0537a-108">V následujícím kódu <xref:System.ServiceModel.Web.WebGetAttribute> je atribut použit `Add` pro operaci, aby bylo zajištěno, že služba reaguje na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="0537a-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="0537a-109">Kód používá GET pro jednoduchost (požadavek HTTP GET můžete vytvořit z libovolného webového prohlížeče).</span><span class="sxs-lookup"><span data-stu-id="0537a-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="0537a-110">Můžete také použít GET a povolit ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="0537a-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="0537a-111">HTTP post je výchozím nastavením při nepřítomnosti `WebGetAttribute` atributu.</span><span class="sxs-lookup"><span data-stu-id="0537a-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>  

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

 <span data-ttu-id="0537a-112">Ukázkový soubor. svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, který ke službě <xref:System.ServiceModel.Description.WebScriptEndpoint> přidá standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="0537a-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="0537a-113">Koncový bod je nakonfigurovaný na prázdné adrese relativní vzhledem k souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="0537a-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="0537a-114">To znamená, že adresa služby je `http://localhost/ServiceModelSamples/service.svc`bez dalších přípon, než je název operace.</span><span class="sxs-lookup"><span data-stu-id="0537a-114">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>  

```svc
<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>
```

 <span data-ttu-id="0537a-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> Je předem nakonfigurovaný tak, aby služba byla přístupná z klientské stránky ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="0537a-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="0537a-116">Následující oddíl v souboru Web. config lze použít k provedení dalších změn konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="0537a-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="0537a-117">Tuto možnost lze odebrat, pokud nejsou vyžadovány žádné další změny.</span><span class="sxs-lookup"><span data-stu-id="0537a-117">It can be removed if no extra changes are required.</span></span>  
  
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
  
 <span data-ttu-id="0537a-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> Nastaví výchozí formát dat pro službu na JSON namísto XML.</span><span class="sxs-lookup"><span data-stu-id="0537a-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="0537a-119">Chcete-li vyvolat službu, přejděte `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` na adresu po dokončení kroků nastavení a sestavení, které jsou uvedeny dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="0537a-119">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="0537a-120">Tato funkce testování je povolena pomocí požadavku HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="0537a-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>  
  
 <span data-ttu-id="0537a-121">Klientská webová stránka SimpleAjaxClientPage. aspx obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na stránku s jedním z těchto tlačítek operace.</span><span class="sxs-lookup"><span data-stu-id="0537a-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="0537a-122">`ScriptManager` Ovládací prvek slouží k vytvoření proxy serveru pro přístup k službě prostřednictvím JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="0537a-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>  

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">  
    <Services>  
        <asp:ServiceReference Path="service.svc" />  
    </Services>  
</asp:ScriptManager>  
```

 <span data-ttu-id="0537a-123">Instance místního proxy serveru a operace jsou vyvolány pomocí následujícího kódu JavaScriptu.</span><span class="sxs-lookup"><span data-stu-id="0537a-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>  

```javascript
// Code for extracting arguments n1 and n2 omitted…  
// Instantiate a service proxy  
var proxy = new SimpleAjaxService.ICalculator();  
// Code for selecting operation omitted…  
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);  
```

 <span data-ttu-id="0537a-124">Pokud je volání služby úspěšné, kód vyvolá `onSuccess` obslužnou rutinu a výsledek operace se zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="0537a-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("result").value = mathResult;  
}
```

> [!IMPORTANT]
>  <span data-ttu-id="0537a-125">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="0537a-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0537a-126">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="0537a-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0537a-127">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="0537a-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0537a-128">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0537a-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`  
