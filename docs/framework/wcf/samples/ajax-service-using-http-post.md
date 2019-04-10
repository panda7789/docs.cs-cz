---
title: Služba AJAX, která používá HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 2bc1722056af4fc71f5f93d92ecd12accd99548f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343243"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="8fa9b-102">Služba AJAX, která používá HTTP POST</span><span class="sxs-lookup"><span data-stu-id="8fa9b-102">AJAX Service Using HTTP POST</span></span>
<span data-ttu-id="8fa9b-103">Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] asynchronní JavaScript a XML (AJAX) služby, která používá HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="8fa9b-104">Služby AJAX je ten, který se dostanete pomocí základního kódu jazyka JavaScript z webového prohlížeče klienta.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="8fa9b-105">Tato ukázka je založena na [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka; jediným rozdílem mezi dvěma vzorky se používá HTTP POST místo HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>  
  
 <span data-ttu-id="8fa9b-106">Podpora pro AJAX ve Windows Communication Foundation (WCF) je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím `ScriptManager` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="8fa9b-107">Příklad použití WCF pomocí ASP.NET AJAX, najdete v článku [Ajax ukázky](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="8fa9b-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fa9b-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8fa9b-109">Tato služba v následujícím příkladu je služba WCF se žádný kód specifický pro AJAX.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>  
  
 <span data-ttu-id="8fa9b-110">Pokud <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut se používá u určité operace, nebo <xref:System.ServiceModel.Web.WebGetAttribute> atribut není použit, je použit výchozí příkaz protokolu HTTP (dále jen "příspěvek").</span><span class="sxs-lookup"><span data-stu-id="8fa9b-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="8fa9b-111">Požadavky POST jsou obtížnější k sestavení kompletních než požadavky GET, ale neukládají do mezipaměti; Použijte požadavky POST pro všechny operace, kde není vhodné ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 <span data-ttu-id="8fa9b-112">Vytvořit koncový bod AJAX na službě s použitím <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, stejně jako v ukázce základní služba AJAX.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="8fa9b-113">Na rozdíl od požadavků GET nejde vyvolat příspěvek služby z prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="8fa9b-114">Například, že přejdete na `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` způsobí chybu, protože služba příspěvek očekává `n1` a `n2` parametry se mají odeslat v textu zprávy ve formátu JSON a ne v adrese URL.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>  
  
 <span data-ttu-id="8fa9b-115">Klient PostAjaxClientPage.aspx webová stránka obsahuje kód technologie ASP.NET se vyvolat službu pokaždé, když uživatel klikne jedno z tlačítek operace na stránce.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="8fa9b-116">Služba odpoví stejným způsobem jako v [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázku s požadavek GET.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8fa9b-117">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8fa9b-118">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="8fa9b-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8fa9b-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8fa9b-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8fa9b-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8fa9b-121">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="8fa9b-121">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8fa9b-122">Zajistěte, aby pokyny k instalaci [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8fa9b-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8fa9b-123">Sestavte řešení PostAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8fa9b-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8fa9b-124">Přejděte na `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (neotevírejte PostAjaxClientPage.aspx v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="8fa9b-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
