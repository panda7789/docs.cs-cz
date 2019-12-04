---
title: Služba AJAX bez konfigurace
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: bf80f00bbca370c973dab9f20024284a465be521
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716201"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="962cd-102">Služba AJAX bez konfigurace</span><span class="sxs-lookup"><span data-stu-id="962cd-102">AJAX Service Without Configuration</span></span>

<span data-ttu-id="962cd-103">Tato ukázka předvádí, jak použít Windows Communication Foundation (WCF) k vytvoření základní služby JavaScriptu (ASP.NET Asynchronous JavaScript and XML) (služba, ke které máte přístup pomocí kódu jazyka JavaScript z klienta webového prohlížeče) bez použití jakékoli konfigurace. možnost.</span><span class="sxs-lookup"><span data-stu-id="962cd-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="962cd-104">Služba používá k automatickému povolení koncového bodu AJAX speciální syntaxi v souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="962cd-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>

<span data-ttu-id="962cd-105">Podpora AJAX ve WCF je optimalizovaná pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku `ScriptManager`.</span><span class="sxs-lookup"><span data-stu-id="962cd-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="962cd-106">Příklad použití WCF s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="962cd-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="962cd-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="962cd-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="962cd-108">Tato ukázka sestaví na základě služby AJAX pomocí HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="962cd-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="962cd-109">Jak je popsáno v ukázce [základní služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> slouží k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="962cd-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>

```text
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<span data-ttu-id="962cd-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> do služby automaticky přidá <xref:System.ServiceModel.Description.WebScriptEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="962cd-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="962cd-111">Pokud není nutné provést žádné změny v konfiguraci koncového bodu, může být oddíl `<system.ServiceModel>` zcela odebrán ze souboru Web. config služby.</span><span class="sxs-lookup"><span data-stu-id="962cd-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="962cd-112">Soubor Web. config obsahuje některá nastavení ASP.NET, která jsou používána souborem ConfigFreeClientPage. aspx.</span><span class="sxs-lookup"><span data-stu-id="962cd-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="962cd-113">V případě, že se nejednalo o tento případ, mohl by být odebrán celý soubor Web. config.</span><span class="sxs-lookup"><span data-stu-id="962cd-113">If that were not the case, the entire Web.config file could be removed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="962cd-114">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="962cd-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="962cd-115">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="962cd-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="962cd-116">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="962cd-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="962cd-117">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="962cd-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="962cd-118">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="962cd-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="962cd-119">Postupujte podle pokynů pro instalaci v [části Postup instalace pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="962cd-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="962cd-120">Sestavte řešení ConfigFreeAjaxService. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="962cd-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="962cd-121">Přejděte na `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (neotevírejte ConfigFreeClientPage. aspx v prohlížeči z adresáře projektu).</span><span class="sxs-lookup"><span data-stu-id="962cd-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>

> [!NOTE]
> <span data-ttu-id="962cd-122">Při spuštění této ukázky Prosím zajistěte, aby anonymní ověřování a ověřování systému Windows nebylo pro složku ServiceModelSamples ve službě IIS povoleno současně.</span><span class="sxs-lookup"><span data-stu-id="962cd-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="962cd-123">V takovém případě prosím zakažte ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="962cd-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="962cd-124">Po spuštění ukázky povolte ověřování systému Windows a spusťte příkaz iisreset.</span><span class="sxs-lookup"><span data-stu-id="962cd-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>

## <a name="see-also"></a><span data-ttu-id="962cd-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="962cd-125">See also</span></span>

- [<span data-ttu-id="962cd-126">Základní služba AJAX</span><span class="sxs-lookup"><span data-stu-id="962cd-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
