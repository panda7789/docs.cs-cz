---
title: "Služba AJAX bez konfigurace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 32879c2b618f3e22960a7828d29601f502a55585
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="9285c-102">Služba AJAX bez konfigurace</span><span class="sxs-lookup"><span data-stu-id="9285c-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="9285c-103">Tento příklad ukazuje, jak používat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vytvořit základní služby ASP.NET asynchronní JavaScript a XML (AJAX) (služba, který je přístupný pomocí kódu jazyka JavaScript z webového prohlížeče klienta) bez použití nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9285c-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="9285c-104">Služba používá speciální syntaxe v souboru .svc automaticky povolení koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="9285c-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="9285c-105">Podpora jazyka AJAX v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je optimalizovaný pro použití s pomocí prvku ASP.NET AJAX `ScriptManager` ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9285c-105">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="9285c-106">Příklad použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí prvku ASP.NET AJAX, najdete v článku [Ajax ukázky](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="9285c-106">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9285c-107">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9285c-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9285c-108">Tato ukázka je založen na AJAX služby pomocí HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="9285c-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="9285c-109">Jak je popsáno v [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázce <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se používá k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="9285c-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```  
  
 <span data-ttu-id="9285c-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>automaticky přidá <xref:System.ServiceModel.Description.WebScriptEndpoint> ke službě.</span><span class="sxs-lookup"><span data-stu-id="9285c-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="9285c-111">Pokud potřebujete provést ke koncovému bodu, žádné změny konfigurace \<systému. ServiceModel > části lze úplně odebrat ze souboru Web.config pro službu.</span><span class="sxs-lookup"><span data-stu-id="9285c-111">If no configuration changes need to be made to the endpoint, the \<system.ServiceModel> section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="9285c-112">Soubor Web.config obsahuje některá nastavení ASP.NET, které jsou používány ConfigFreeClientPage.aspx.</span><span class="sxs-lookup"><span data-stu-id="9285c-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="9285c-113">Pokud je tento není tento případ, může odebrat celý soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="9285c-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9285c-114">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9285c-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9285c-115">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9285c-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9285c-116">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9285c-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9285c-117">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9285c-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9285c-118">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="9285c-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9285c-119">Ujistěte se, že můžete provádět pokynů pro instalaci v [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9285c-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9285c-120">Sestavte řešení ConfigFreeAjaxService.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9285c-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9285c-121">Přejděte na http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (neotevírejte ConfigFreeClientPage.aspx v prohlížeči z v adresáři projektu).</span><span class="sxs-lookup"><span data-stu-id="9285c-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9285c-122">Při spuštění této ukázce, Zkontrolujte prosím, že anonymní ověřování a ověřování systému Windows nejsou povolené současně ServiceModelSamples složky ve službě IIS.</span><span class="sxs-lookup"><span data-stu-id="9285c-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="9285c-123">Pokud tomu tak je, zakažte ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9285c-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="9285c-124">Po spuštění vzorového povolit ověřování systému Windows a spusťte "příkaz iisreset".</span><span class="sxs-lookup"><span data-stu-id="9285c-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9285c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9285c-125">See Also</span></span>  
 [<span data-ttu-id="9285c-126">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="9285c-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
