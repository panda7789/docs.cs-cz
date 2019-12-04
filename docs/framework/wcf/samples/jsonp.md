---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 82fa0bb09ebdf3ca2325872c2b884f4940de17ed
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715722"
---
# <a name="jsonp"></a><span data-ttu-id="53b23-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="53b23-102">JSONP</span></span>
<span data-ttu-id="53b23-103">Tato ukázka demonstruje, jak podporovat JSON s odsazením (JSONP) ve službách WCF REST.</span><span class="sxs-lookup"><span data-stu-id="53b23-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="53b23-104">JSONP je konvence, která se používá k vyvolání skriptů mezi doménami generováním značek skriptu v aktuálním dokumentu.</span><span class="sxs-lookup"><span data-stu-id="53b23-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="53b23-105">Výsledek je vrácen v zadané funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="53b23-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="53b23-106">JSONP je založen na nápadu, který značky, jako je `<script src="http://..." >`, může vyhodnotit skripty z jakékoli domény a skript načtený těmito značkami je vyhodnocen v rámci oboru, ve kterém již mohou být definovány jiné funkce.</span><span class="sxs-lookup"><span data-stu-id="53b23-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="53b23-107">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="53b23-107">Demonstrates</span></span>
 <span data-ttu-id="53b23-108">Skriptování mezi doménami pomocí JSONP.</span><span class="sxs-lookup"><span data-stu-id="53b23-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="53b23-109">Účely</span><span class="sxs-lookup"><span data-stu-id="53b23-109">Discussion</span></span>
 <span data-ttu-id="53b23-110">Ukázka obsahuje webovou stránku, která dynamicky přidá blok skriptu po vykreslení stránky v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="53b23-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="53b23-111">Tento blok skriptu volá službu WCF REST, která má jedinou operaci, `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="53b23-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="53b23-112">Služba WCF REST vrátí jméno a adresu zákazníka zabalené do názvu funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="53b23-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="53b23-113">Pokud služba WCF REST reaguje, je funkce zpětného volání na webové stránce vyvolána pomocí zákaznických dat a funkce zpětného volání zobrazí data na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="53b23-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="53b23-114">Vložení značky Script a provedení funkce zpětného volání je automaticky zpracováno ovládacím prvkem ASP.NET AJAX ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="53b23-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="53b23-115">Vzor použití je stejný jako u všech proxy ASP.NET AJAX, s přidáním jednoho řádku pro povolení JSONP, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="53b23-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="53b23-116">Webová stránka může zavolat službu WCF REST, protože služba používá <xref:System.ServiceModel.Description.WebScriptEndpoint> s `crossDomainScriptAccessEnabled` nastavenou na `true`.</span><span class="sxs-lookup"><span data-stu-id="53b23-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="53b23-117">Obě tyto konfigurace jsou provedeny v souboru Web. config pod prvkem \<System. serviceModel >.</span><span class="sxs-lookup"><span data-stu-id="53b23-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

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

 <span data-ttu-id="53b23-118">ScriptManager spravuje interakci se službou a skrývá složitost ruční implementace přístupu JSONP.</span><span class="sxs-lookup"><span data-stu-id="53b23-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="53b23-119">Pokud je `crossDomainScriptAccessEnabled` nastaveno na `true` a formát odpovědi pro operaci je JSON, infrastruktura WCF zkontroluje identifikátor URI žádosti pro parametr řetězce dotazu zpětného volání a zabalí odpověď JSON s hodnotou parametru řetězce dotazu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="53b23-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="53b23-120">V ukázce webová stránka volá službu WCF REST s následujícím identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="53b23-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="53b23-121">Vzhledem k tomu, že parametr řetězce dotazu zpětného volání má hodnotu `JsonPCallback`, služba WCF vrátí odpověď JSONP zobrazenou v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="53b23-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="53b23-122">Tato odpověď JSONP zahrnuje zákaznická data formátovaná jako JSON, zabalená pomocí názvu funkce zpětného volání, kterou požaduje požadovaná webová stránka.</span><span class="sxs-lookup"><span data-stu-id="53b23-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="53b23-123">ScriptManager spustí toto zpětné volání pomocí značky skriptu, aby provedl požadavek mezi doménami, a poté předává výsledek obslužné rutině úspěch, která byla předána do operace GetCustomer v proxy ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="53b23-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="53b23-124">Ukázka se skládá ze dvou webových aplikací ASP.NET: jeden obsahuje pouze službu WCF a druhý obsahuje webovou stránku. aspx, která volá službu.</span><span class="sxs-lookup"><span data-stu-id="53b23-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="53b23-125">Při spuštění řešení bude Visual Studio 2012 hostovat tyto dvě weby na různých portech, čímž se vytvoří prostředí, ve kterém je služba a klient v různých doménách aktivní.</span><span class="sxs-lookup"><span data-stu-id="53b23-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="53b23-126">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="53b23-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="53b23-127">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="53b23-127">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="53b23-128">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="53b23-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="53b23-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="53b23-129">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="53b23-130">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="53b23-130">To run the sample</span></span>  
  
1. <span data-ttu-id="53b23-131">Otevřete řešení pro ukázku JSONP.</span><span class="sxs-lookup"><span data-stu-id="53b23-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="53b23-132">Stisknutím klávesy F5 spustíte `http://localhost:26648/JSONPClientPage.aspx` v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="53b23-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="53b23-133">Všimněte si, že po načtení stránky se textové vstupy pro "název" a "adresa" vyplní hodnotami.</span><span class="sxs-lookup"><span data-stu-id="53b23-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="53b23-134">Tyto hodnoty byly zadány z volání služby WCF poté, co prohlížeč dokončil vykreslování stránky.</span><span class="sxs-lookup"><span data-stu-id="53b23-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
