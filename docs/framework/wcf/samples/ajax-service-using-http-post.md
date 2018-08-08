---
title: Služba AJAX, která používá HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: f904a26d87a21a931035b45261dbcd970f7d63a1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804105"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="f2c9a-102">Služba AJAX, která používá HTTP POST</span><span class="sxs-lookup"><span data-stu-id="f2c9a-102">AJAX Service Using HTTP POST</span></span>
<span data-ttu-id="f2c9a-103">Tento příklad ukazuje, jak pomocí služby Windows Communication Foundation (WCF) můžete vytvořit [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] asynchronní JavaScript a XML (AJAX) službu, která používá HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="f2c9a-104">Služby AJAX je ten, který lze přistupovat pomocí základního kódu jazyka JavaScript z webového prohlížeče klienta.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="f2c9a-105">Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázku; jediným rozdílem mezi dvěma vzorky je použití HTTP POST namísto metody GET protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>  
  
 <span data-ttu-id="f2c9a-106">Podpora jazyka AJAX ve Windows Communication Foundation (WCF) je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX `ScriptManager` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="f2c9a-107">Příklad WCF pomocí prvku ASP.NET AJAX, najdete v článku [Ajax ukázky](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="f2c9a-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2c9a-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f2c9a-109">Služba v následující ukázce je služby WCF s žádné kódu pro konkrétní jazyk AJAX.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>  
  
 <span data-ttu-id="f2c9a-110">Pokud <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut se používá u určité operace, nebo <xref:System.ServiceModel.Web.WebGetAttribute> atribut není použit, bude použita výchozí akce HTTP (dále jen "příspěvek").</span><span class="sxs-lookup"><span data-stu-id="f2c9a-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="f2c9a-111">Požadavky POST jsou těžší vytvořit než požadavky GET, ale nejsou v mezipaměti; pomocí požadavků POST pro všechny operace, kde není vhodná ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 <span data-ttu-id="f2c9a-112">Vytvoření AJAX koncový bod služby pomocí <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, jen jako ukázka základní služba AJAX.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="f2c9a-113">Na rozdíl od požadavky GET nemohou vyvolat POST služby z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="f2c9a-114">Například přejdete na http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 skončí chybou, protože služba POST očekává `n1` a `n2` parametry pro odeslání v textu zprávy – ve formátu JSON – a ne v adrese URL.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-114">For example, navigating to http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200 results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body—in the JSON format—and not in the URL.</span></span>  
  
 <span data-ttu-id="f2c9a-115">Klient PostAjaxClientPage.aspx webová stránka obsahuje kód ASP.NET k vyvolání služby vždy, když uživatel klikne na jednu operaci tlačítek na stránce.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="f2c9a-116">Služba odpovídá stejným způsobem jako v [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázku s požadavek GET.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f2c9a-117">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f2c9a-118">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f2c9a-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f2c9a-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2c9a-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f2c9a-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f2c9a-121">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="f2c9a-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f2c9a-122">Ujistěte se, že provádíte pokynů pro instalaci [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2c9a-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f2c9a-123">Sestavte řešení PostAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f2c9a-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f2c9a-124">Přejděte na http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (neotevírejte PostAjaxClientPage.aspx v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="f2c9a-124">Navigate to http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c9a-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2c9a-125">See Also</span></span>
