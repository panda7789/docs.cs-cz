---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 6b5b42285539c2334bccaa04e1ba179d2cf0046c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183574"
---
# <a name="jsonp"></a><span data-ttu-id="bd750-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="bd750-102">JSONP</span></span>
<span data-ttu-id="bd750-103">Tato ukázka ukazuje, jak podporovat JSON s padding (JSONP) ve službách WCF REST.</span><span class="sxs-lookup"><span data-stu-id="bd750-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="bd750-104">JSONP je konvence používaná k vyvolání skriptů mezi doménami generováním značek skriptů v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="bd750-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="bd750-105">Výsledek je vrácen v zadané funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bd750-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="bd750-106">JSONP je založen na myšlence, že značky, jako `<script src="http://..." >` jsou můžete vyhodnotit skripty z libovolné domény a skript načtený těmito značkami je vyhodnocen v rámci oboru, ve kterém již mohou být definovány další funkce.</span><span class="sxs-lookup"><span data-stu-id="bd750-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bd750-107">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="bd750-107">Demonstrates</span></span>
 <span data-ttu-id="bd750-108">Skriptování mezi doménami pomocí jsonp.</span><span class="sxs-lookup"><span data-stu-id="bd750-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="bd750-109">Diskuse</span><span class="sxs-lookup"><span data-stu-id="bd750-109">Discussion</span></span>
 <span data-ttu-id="bd750-110">Ukázka obsahuje webovou stránku, která dynamicky přidává blok skriptu po vykreslení stránky v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="bd750-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="bd750-111">Tento blok skriptu volá službu WCF `GetCustomer`REST, která má jednu operaci .</span><span class="sxs-lookup"><span data-stu-id="bd750-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="bd750-112">Služba WCF REST vrátí jméno a adresu zákazníka zabalené v názvu funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bd750-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="bd750-113">Když služba WCF REST odpoví, funkce zpětného volání na webové stránce je vyvolána s daty zákazníka a funkce zpětného volání zobrazí data na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="bd750-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="bd750-114">Vkládání značky skriptu a spuštění funkce zpětného volání je automaticky zpracováno ovládacím prvkem ASP.NET AJAX ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="bd750-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="bd750-115">Vzor použití je stejný jako u všech ASP.NET proxy ajax, s přidáním jednoho řádku povolit JSONP, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="bd750-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="bd750-116">Webová stránka může volat službu WCF REST, `crossDomainScriptAccessEnabled` protože `true`služba používá sadu with nastavenou <xref:System.ServiceModel.Description.WebScriptEndpoint> na .</span><span class="sxs-lookup"><span data-stu-id="bd750-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="bd750-117">Obě tyto konfigurace jsou prováděny v souboru Web.config pod elementem \<system.serviceModel>.</span><span class="sxs-lookup"><span data-stu-id="bd750-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

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

 <span data-ttu-id="bd750-118">ScriptManager spravuje interakci se službou a skryje složitost ruční implementace přístupu JSONP.</span><span class="sxs-lookup"><span data-stu-id="bd750-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="bd750-119">Pokud `crossDomainScriptAccessEnabled` je `true` nastavena na a formát odpovědi pro operaci je JSON, WCF infrastruktury zkontroluje URI požadavku na parametr řetězce dotazu zpětného volání a zalomí odpověď JSON s hodnotou parametru řetězce dotazu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bd750-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="bd750-120">V ukázce webová stránka volá službu WCF REST s následujícím identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="bd750-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="bd750-121">Vzhledem k tomu, že parametr `JsonPCallback`řetězce dotazu zpětného volání má hodnotu , vrátí služba WCF odpověď JSONP zobrazenou v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bd750-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="bd750-122">Tato odpověď JSONP zahrnuje zákaznická data formátovaná jako JSON, zabalená s názvem funkce zpětného volání, který požadovala webová stránka.</span><span class="sxs-lookup"><span data-stu-id="bd750-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="bd750-123">ScriptManager spustí toto zpětné volání pomocí značky skriptu k provedení požadavku mezi doménami a poté předá výsledek obslužné rutině onSuccess, která byla předána operaci GetCustomer ASP.NET proxy ajax.</span><span class="sxs-lookup"><span data-stu-id="bd750-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="bd750-124">Ukázka se skládá ze dvou ASP.NET webových aplikací: jedna obsahuje pouze službu WCF a druhá obsahuje webovou stránku ASPX, která službu volá.</span><span class="sxs-lookup"><span data-stu-id="bd750-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="bd750-125">Při spuštění řešení visual studio 2012 bude hostit dva weby na různých portech, což vytvoří prostředí, kde služba a klient žijí v různých doménách.</span><span class="sxs-lookup"><span data-stu-id="bd750-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd750-126">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="bd750-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bd750-127">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="bd750-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bd750-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bd750-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bd750-129">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bd750-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="bd750-130">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="bd750-130">To run the sample</span></span>  
  
1. <span data-ttu-id="bd750-131">Otevřete řešení pro ukázku JSONP.</span><span class="sxs-lookup"><span data-stu-id="bd750-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="bd750-132">Stisknutím klávesy `http://localhost:26648/JSONPClientPage.aspx` F5 se spustí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="bd750-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="bd750-133">Všimněte si, že po načtení stránky jsou textové vstupy pro "Name" a "Adresa" naplněny hodnotami.</span><span class="sxs-lookup"><span data-stu-id="bd750-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="bd750-134">Tyto hodnoty byly dodány z volání služby WCF po dokončení vykreslování stránky prohlížečem.</span><span class="sxs-lookup"><span data-stu-id="bd750-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
