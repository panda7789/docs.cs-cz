---
title: Služba AJAX, která používá HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 143585b40a493983b7265971a17224165de6f36d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575885"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="26f86-102">Služba AJAX, která používá HTTP POST</span><span class="sxs-lookup"><span data-stu-id="26f86-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="26f86-103">Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření služby ASP.NET Asynchronous JavaScript a XML (AJAX), která používá HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="26f86-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="26f86-104">Služba AJAX je ta, ke které můžete přistupovat pomocí základního kódu JavaScriptu z klienta webového prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="26f86-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="26f86-105">Tato ukázka sestaví na [základní ukázce služby AJAX](basic-ajax-service.md) . Jediným rozdílem mezi těmito dvěma ukázkami je použití HTTP POST místo HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="26f86-105">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="26f86-106">Podpora AJAX v Windows Communication Foundation (WCF) je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="26f86-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="26f86-107">Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="26f86-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="26f86-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="26f86-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="26f86-109">Služba v následující ukázce je služba WCF bez kódu specifického pro AJAX.</span><span class="sxs-lookup"><span data-stu-id="26f86-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="26f86-110">Pokud <xref:System.ServiceModel.Web.WebInvokeAttribute> je atribut použit pro operaci, nebo <xref:System.ServiceModel.Web.WebGetAttribute> atribut není použit, je použita výchozí operace HTTP ("post").</span><span class="sxs-lookup"><span data-stu-id="26f86-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="26f86-111">Žádosti POST jsou těžší vytvořit než požadavky GET, ale nejsou ukládány do mezipaměti. pro všechny operace, u kterých není ukládání do mezipaměti vhodné, použijte požadavky POST.</span><span class="sxs-lookup"><span data-stu-id="26f86-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="26f86-112">Vytvořte koncový bod AJAX ve službě pomocí nástroje <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , stejně jako v ukázce základní služby AJAX.</span><span class="sxs-lookup"><span data-stu-id="26f86-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="26f86-113">Na rozdíl od požadavků GET nelze vyvolat POST Services z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="26f86-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="26f86-114">Například při přechodu na výsledky dojde k `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` chybě, protože post Service očekává `n1` `n2` odeslání parametrů a v těle zprávy ve formátu JSON, a ne v adrese URL.</span><span class="sxs-lookup"><span data-stu-id="26f86-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="26f86-115">Klientská webová stránka PostAjaxClientPage. aspx obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na stránku s jedním z těchto tlačítek operace.</span><span class="sxs-lookup"><span data-stu-id="26f86-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="26f86-116">Služba reaguje stejným způsobem jako v ukázce [základní služby AJAX](basic-ajax-service.md) s požadavkem Get.</span><span class="sxs-lookup"><span data-stu-id="26f86-116">The service responds in the same way as in the [Basic AJAX Service](basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26f86-117">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="26f86-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="26f86-118">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="26f86-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="26f86-119">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="26f86-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="26f86-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="26f86-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="26f86-121">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="26f86-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="26f86-122">Ujistěte se, že jste provedli postup instalace s pokyny [pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26f86-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="26f86-123">Sestavte řešení PostAjaxService. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="26f86-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="26f86-124">Přejděte na adresu `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (v prohlížeči z adresáře projektu neotevírejte PostAjaxClientPage. aspx).</span><span class="sxs-lookup"><span data-stu-id="26f86-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
