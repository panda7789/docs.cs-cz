---
title: JSONP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9a9355c223d3d37811383d52d64f0ac6ddeeaea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="jsonp"></a><span data-ttu-id="4829f-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="4829f-102">JSONP</span></span>
<span data-ttu-id="4829f-103">Tento příklad ukazuje, jak podporovala JSON s odsazení (JSONP) ve službě WCF REST services.</span><span class="sxs-lookup"><span data-stu-id="4829f-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="4829f-104">JSONP je konvence používaná k vyvolání skripty napříč doménami a generování značek skriptu v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4829f-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="4829f-105">Výsledkem je vrácený v zadané zpětného volání funkce.</span><span class="sxs-lookup"><span data-stu-id="4829f-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="4829f-106">JSONP je založena na nápad, které přidá značky, jako \<skript src = "http:/ /..." > můžete vyhodnotit skriptů z jakékoli domény a skriptu načíst tyto značky je vyhodnocován v rámci oboru, ve kterém může již definována dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="4829f-106">JSONP is based on the idea that tags such as \<script src="http://..." > can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="4829f-107">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="4829f-107">Demonstrates</span></span>  
 <span data-ttu-id="4829f-108">Mezi doménami skriptování s JSONP.</span><span class="sxs-lookup"><span data-stu-id="4829f-108">Cross-domain scripting with JSONP.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="4829f-109">Diskusní</span><span class="sxs-lookup"><span data-stu-id="4829f-109">Discussion</span></span>  
 <span data-ttu-id="4829f-110">Ukázka zahrnuje webové stránky, která dynamicky přidá blok skriptu po vykreslena stránku v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4829f-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="4829f-111">Tento blok skriptu volání WCF REST služba, která má jednu operaci `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="4829f-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="4829f-112">Služby WCF REST vrátí název a adresu uzavřen do název funkce zpětného volání zákazníka.</span><span class="sxs-lookup"><span data-stu-id="4829f-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="4829f-113">Pokud službu WCF REST odpoví, vyvolání funkce zpětného volání na webové stránce zákaznická data a funkce zpětného volání zobrazí data na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="4829f-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="4829f-114">Vkládání značky script a spouštění funkce zpětného volání automaticky zpracováván pomocí prvku ASP.NET AJAX ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="4829f-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="4829f-115">Vzor používání je stejný jako s všechny proxy servery prvku ASP.NET AJAX, a uveďte jeden řádek povolit JSONP, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="4829f-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 <span data-ttu-id="4829f-116">Webové stránky můžete volat službu WCF REST, protože služba používá technologii <xref:System.ServiceModel.Description.WebScriptEndpoint> s `crossDomainScriptAccessEnabled` nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="4829f-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="4829f-117">Obě tyto konfigurace se provádějí v souboru Web.config pod \<system.serviceModel > elementu.</span><span class="sxs-lookup"><span data-stu-id="4829f-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>  
  
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
  
 <span data-ttu-id="4829f-118">ScriptManager spravuje interakci se službou a rychle skrývá složitosti implementace ručně JSONP přístup.</span><span class="sxs-lookup"><span data-stu-id="4829f-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="4829f-119">Při `crossDomainScriptAccessEnabled` je nastaven na `true` a odpovědi formátu JSON, je operace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastruktury zkontroluje identifikátor URI požadavku pro parametr řetězce dotazu zpětného volání a zabalí odpověď JSON s hodnotou dotazu zpětného volání parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="4829f-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="4829f-120">V ukázce webová stránka volá službu WCF REST s následující identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="4829f-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 <span data-ttu-id="4829f-121">Vzhledem k tomu, že parametr řetězce dotazu zpětného volání má hodnotu `JsonPCallback`, služby WCF vrátí odpověď JSONP vidět v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4829f-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 <span data-ttu-id="4829f-122">Tato odpověď JSONP obsahuje data zákazníků formátu JSON, obklopeno název funkce zpětného volání, která požadované webové stránky.</span><span class="sxs-lookup"><span data-stu-id="4829f-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="4829f-123">ScriptManager bude provedení tohoto zpětného volání pomocí značky script k provádění požadavku napříč doménami a výsledek předat onSuccess obslužná rutina, která byla předána operaci GetCustomer proxy prvku ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="4829f-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>  
  
 <span data-ttu-id="4829f-124">Ukázkový soubor obsahuje dva webové aplikace ASP.NET: jeden obsahuje jenom [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby a jinou obsahuje webová stránka .aspx, který zavolá službu.</span><span class="sxs-lookup"><span data-stu-id="4829f-124">The sample consists of two ASP.NET web applications: one contains just a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="4829f-125">Při spuštění tohoto řešení [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] bude hostitelem dvou webů na jiné porty, které vytvoří prostředí, kde klienta a služby za provozu na různých doménách.</span><span class="sxs-lookup"><span data-stu-id="4829f-125">When running the solution, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4829f-126">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="4829f-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4829f-127">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4829f-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4829f-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4829f-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4829f-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4829f-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="4829f-130">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="4829f-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="4829f-131">Otevřete řešení pro ukázku JSONP.</span><span class="sxs-lookup"><span data-stu-id="4829f-131">Open the solution for the JSONP Sample.</span></span>  
  
2.  <span data-ttu-id="4829f-132">Stisknutím klávesy F5 spusťte HYPERLINK "http://localhost:26648/JSONPClientPage.aspx" http://localhost:26648/JSONPClientPage.aspx v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4829f-132">Press F5 to launch  HYPERLINK "http://localhost:26648/JSONPClientPage.aspx" http://localhost:26648/JSONPClientPage.aspx in the browser.</span></span>  
  
3.  <span data-ttu-id="4829f-133">Všimněte si, že po načtení stránky vstupy text "Název" a "Address" jsou naplněny podle hodnot.</span><span class="sxs-lookup"><span data-stu-id="4829f-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="4829f-134">Tyto hodnoty nebyly zadány volání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby po vykreslení stránky v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4829f-134">These values were supplied from a call to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service after the browser finished rendering the page.</span></span>
