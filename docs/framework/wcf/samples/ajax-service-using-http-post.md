---
title: Služba AJAX, která používá HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c5e5de34573fbfc8a5c6e9607d10881941a9bed5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972025"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="4fb85-102">Služba AJAX, která používá HTTP POST</span><span class="sxs-lookup"><span data-stu-id="4fb85-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="4fb85-103">Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření služby ASP.NET Asynchronous JavaScript a XML (AJAX), která používá HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="4fb85-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="4fb85-104">Služba AJAX je ta, ke které můžete přistupovat pomocí základního kódu JavaScriptu z klienta webového prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="4fb85-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="4fb85-105">Tato ukázka sestaví na [základní ukázce služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) . Jediným rozdílem mezi těmito dvěma ukázkami je použití HTTP POST místo HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="4fb85-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="4fb85-106">Podpora AJAX v Windows Communication Foundation (WCF) je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4fb85-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="4fb85-107">Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="4fb85-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4fb85-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4fb85-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="4fb85-109">Služba v následující ukázce je služba WCF bez kódu specifického pro AJAX.</span><span class="sxs-lookup"><span data-stu-id="4fb85-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="4fb85-110">Pokud je <xref:System.ServiceModel.Web.WebGetAttribute> atribut použit pro operaci, nebo atribut není použit, je použita výchozí operace HTTP ("post"). <xref:System.ServiceModel.Web.WebInvokeAttribute></span><span class="sxs-lookup"><span data-stu-id="4fb85-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="4fb85-111">Žádosti POST jsou těžší vytvořit než požadavky GET, ale nejsou ukládány do mezipaměti. pro všechny operace, u kterých není ukládání do mezipaměti vhodné, použijte požadavky POST.</span><span class="sxs-lookup"><span data-stu-id="4fb85-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="4fb85-112">Vytvořte koncový bod AJAX ve službě pomocí nástroje <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, stejně jako v ukázce základní služby AJAX.</span><span class="sxs-lookup"><span data-stu-id="4fb85-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="4fb85-113">Na rozdíl od požadavků GET nelze vyvolat POST Services z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="4fb85-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="4fb85-114">Například při přechodu na výsledky dojde `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` k chybě, protože post Service `n1` očekává odeslání parametrů a `n2` v těle zprávy ve formátu JSON, a ne v adrese URL.</span><span class="sxs-lookup"><span data-stu-id="4fb85-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="4fb85-115">Klientská webová stránka PostAjaxClientPage. aspx obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na stránku s jedním z těchto tlačítek operace.</span><span class="sxs-lookup"><span data-stu-id="4fb85-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="4fb85-116">Služba reaguje stejným způsobem jako v ukázce [základní služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) s požadavkem Get.</span><span class="sxs-lookup"><span data-stu-id="4fb85-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4fb85-117">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4fb85-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4fb85-118">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4fb85-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="4fb85-119">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="4fb85-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4fb85-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4fb85-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4fb85-121">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4fb85-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4fb85-122">Ujistěte se, že jste provedli postup instalace s pokyny [pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fb85-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="4fb85-123">Sestavte řešení PostAjaxService. sln, jak je popsáno v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4fb85-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="4fb85-124">Přejděte na `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` adresu (v prohlížeči z adresáře projektu neotevírejte PostAjaxClientPage. aspx).</span><span class="sxs-lookup"><span data-stu-id="4fb85-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
