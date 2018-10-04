---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 0e284ee6cce4ab513c03e7be402cc9c0f0c4ee1a
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581911"
---
# <a name="jsonp"></a><span data-ttu-id="9374d-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="9374d-102">JSONP</span></span>
<span data-ttu-id="9374d-103">Tato ukázka předvádí, jak podporovat JSON s odsazení (JSONP) služby WCF REST.</span><span class="sxs-lookup"><span data-stu-id="9374d-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="9374d-104">JSONP je konvence používaná k vyvolání mezi doménami skriptů a generování značek skriptu v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9374d-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="9374d-105">Výsledek se vrátí v zadané zpětného volání funkce.</span><span class="sxs-lookup"><span data-stu-id="9374d-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="9374d-106">JSONP vychází z myšlenky, které přidá značky, jako `<script src="http://..." >` můžete vyhodnotit skriptů z jakékoli domény a skript načte tyto visačky se vyhodnotí v rámci oboru, ve kterém může již definována dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="9374d-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="9374d-107">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="9374d-107">Demonstrates</span></span>
 <span data-ttu-id="9374d-108">Mezi doménami skriptování s JSONP.</span><span class="sxs-lookup"><span data-stu-id="9374d-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="9374d-109">Diskuse</span><span class="sxs-lookup"><span data-stu-id="9374d-109">Discussion</span></span>
 <span data-ttu-id="9374d-110">Ukázka zahrnuje webovou stránku, která dynamicky přidá blok skriptu po byl vykreslen na stránce v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="9374d-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="9374d-111">Tento blok skriptu volání služby WCF REST, který má jednu operaci `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="9374d-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="9374d-112">Služba WCF REST vrátí název zákazníka a adresa zabalené v názvu funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="9374d-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="9374d-113">Pokud odpovídá službě WCF REST, je vyvolána funkce zpětného volání na webové stránce s zákaznická data a funkce zpětného volání zobrazí data na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="9374d-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="9374d-114">Vkládání značky skriptu a provádění funkce zpětného volání je automaticky zpracována ovládacího prvku ScriptManager technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="9374d-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="9374d-115">Vzor využití je stejná jako u všech proxy technologie ASP.NET AJAX, a uveďte jeden řádek umožňující JSONP, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="9374d-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="9374d-116">Webové stránky můžete volat službu WCF REST, protože je používán službou <xref:System.ServiceModel.Description.WebScriptEndpoint> s `crossDomainScriptAccessEnabled` nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="9374d-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="9374d-117">Oba tyto konfigurace se provádí v souboru Web.config v rámci \<system.serviceModel > element.</span><span class="sxs-lookup"><span data-stu-id="9374d-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 <span data-ttu-id="9374d-118">Správce skriptů spravuje interakci se službou a maskuje složitost ručně implementace JSONP přístup okamžitě.</span><span class="sxs-lookup"><span data-stu-id="9374d-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="9374d-119">Když `crossDomainScriptAccessEnabled` je nastavena na `true` a formátu odpovědi pro operaci je JSON, infrastruktura WCF zkontroluje identifikátor URI požadavku pro parametr řetězce dotazu zpětného volání a zabalí odpověď JSON s hodnotou řetězce dotazu zpětného volání parametr.</span><span class="sxs-lookup"><span data-stu-id="9374d-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="9374d-120">Ve vzorku volá webovou stránku služby WCF REST s následujícím identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="9374d-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="9374d-121">Protože má hodnotu parametru řetězce dotazu zpětného volání `JsonPCallback`, služba WCF vrátí odpověď JSONP je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9374d-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="9374d-122">Tato odpověď JSONP obsahuje zákaznická data naformátovaná jako JSON zabalena název funkce zpětného volání, která požadované webové stránky.</span><span class="sxs-lookup"><span data-stu-id="9374d-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="9374d-123">Ovládacímu prvku ScriptManager spustí toto zpětné volání pomocí značky skriptu k provedení žádosti napříč doménami a předat výsledek do onSuccess obslužná rutina, která byla předána GetCustomer operace proxy technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="9374d-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="9374d-124">Ukázka se skládá ze dvou webové aplikace ASP.NET: jeden obsahuje jenom službu WCF a obsahuje jiný webová stránka .aspx, která volá službu.</span><span class="sxs-lookup"><span data-stu-id="9374d-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="9374d-125">Při spuštění řešení, Visual Studio 2012 hostovat dva weby na jiném portu, který vytvoří prostředí, ve kterém klienta a služby live v různých doménách.</span><span class="sxs-lookup"><span data-stu-id="9374d-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="9374d-126">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="9374d-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9374d-127">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9374d-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9374d-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9374d-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9374d-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9374d-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="9374d-130">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="9374d-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="9374d-131">Otevřete řešení pro ukázku JSONP.</span><span class="sxs-lookup"><span data-stu-id="9374d-131">Open the solution for the JSONP Sample.</span></span>  
  
2.  <span data-ttu-id="9374d-132">Stisknutím klávesy F5 spusťte `http://localhost:26648/JSONPClientPage.aspx` v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="9374d-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3.  <span data-ttu-id="9374d-133">Všimněte si, že po načtení stránky textovými vstupy pro "Name" a "Address" se vyplní podle hodnot.</span><span class="sxs-lookup"><span data-stu-id="9374d-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="9374d-134">Tyto hodnoty byly zadány volání služby WCF po vykreslení stránky v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="9374d-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
