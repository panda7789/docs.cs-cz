---
title: Služby WCF a Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 93663cbc33b6fab9b34bb02187e5b04192f5c13d
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715269"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="4d0c9-102">Služby WCF a Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="4d0c9-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="4d0c9-103">Tato ukázka předvádí, jak použít analytické trasování v Windows Communication Foundation (WCF) k vygenerování událostí v trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="4d0c9-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="4d0c9-104">Analytická trasování jsou události vydávané na klíčových místech v zásobníku WCF, které umožňují řešení potíží se službami WCF v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="4d0c9-105">Analytická trasování ve službách WCF je trasování, které je možné zapnout v produkčním prostředí s minimálním dopadem na výkon.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="4d0c9-106">Tato trasování jsou generována jako události v relaci trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="4d0c9-107">Tato ukázka obsahuje základní službu WCF, ve které jsou události emitovány ze služby do protokolu událostí, který lze zobrazit pomocí Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="4d0c9-108">Je také možné spustit vyhrazenou relaci ETW, která naslouchá událostem ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="4d0c9-109">Ukázka obsahuje skript pro vytvoření vyhrazené relace trasování událostí pro Windows, která ukládá události do binárního souboru, který je možné číst pomocí Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="4d0c9-110">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="4d0c9-110">To use this sample</span></span>

1. <span data-ttu-id="4d0c9-111">Pomocí sady Visual Studio 2012 otevřete soubor řešení EtwAnalyticTraceSample. sln.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="4d0c9-112">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="4d0c9-113">Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="4d0c9-114">Ve webovém prohlížeči klikněte na **Kalkulačka. svc**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="4d0c9-115">V prohlížeči by se měl zobrazit identifikátor URI dokumentu WSDL pro službu.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="4d0c9-116">Zkopírujte tento identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-116">Copy that URI.</span></span>

     <span data-ttu-id="4d0c9-117">Ve výchozím nastavení služba zahajuje naslouchání požadavkům na portu 1378 `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="4d0c9-118">Spusťte testovacího klienta WCF (WcfTestClient. exe).</span><span class="sxs-lookup"><span data-stu-id="4d0c9-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="4d0c9-119">Testovací klient služby WCF (WcfTestClient. exe) je umístěný na adrese `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="4d0c9-120">Výchozí instalační adresář sady Visual Studio 2012 je `C:\Program Files\Microsoft Visual Studio 10.0`.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="4d0c9-121">V rámci testovacího klienta WCF přidejte službu tak, že vyberete **soubor**a pak **přidáte službu**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="4d0c9-122">Do vstupního pole přidejte adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="4d0c9-123">Výchozí hodnota je `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="4d0c9-124">Otevřete aplikaci Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="4d0c9-125">Před vyvoláním služby spusťte Prohlížeč událostí a zajistěte, aby protokol událostí naslouchal sledování událostí vygenerovaných ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="4d0c9-126">V nabídce **Start** vyberte **Nástroje pro správu**a potom **Prohlížeč událostí**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="4d0c9-127">Povolte protokoly pro **analýzu** a **ladění** .</span><span class="sxs-lookup"><span data-stu-id="4d0c9-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="4d0c9-128">Ve stromovém zobrazení v Prohlížeč událostí přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="4d0c9-129">Klikněte pravým tlačítkem na **aplikační server – aplikace**, vyberte **Zobrazit**a pak **Zobrazte protokoly o analýze a ladění**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="4d0c9-130">Zajistěte, aby byla zaškrtnuta možnost **Zobrazit protokoly o analýze a ladění** .</span><span class="sxs-lookup"><span data-stu-id="4d0c9-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="4d0c9-131">Povolte **analytický** protokol.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="4d0c9-132">Ve stromovém zobrazení v Prohlížeč událostí přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="4d0c9-133">Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="4d0c9-134">Testování služby</span><span class="sxs-lookup"><span data-stu-id="4d0c9-134">To test the service</span></span>

1. <span data-ttu-id="4d0c9-135">Přepněte zpátky na testovacího klienta WCF a dvakrát klikněte na `Divide` a ponechte výchozí hodnoty, které určují jmenovatele 0.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="4d0c9-136">Pokud je jmenovatel 0, vyvolá služba chybu.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="4d0c9-137">Sledujte události emitované ze služby.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="4d0c9-138">Přepněte zpět na Prohlížeč událostí a přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="4d0c9-139">Klikněte pravým tlačítkem na možnost **analytické** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="4d0c9-140">Události analytického trasování WCF se zobrazí v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="4d0c9-141">Všimněte si, že protože služba vyvolala chybu, zobrazí se v prohlížeči událostí událost trasování chyby.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="4d0c9-142">Opakujte kroky 1 a 2, ale s platnými vstupy.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="4d0c9-143">Hodnota parametru `N2` může být libovolné číslo jiné než 0.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="4d0c9-144">Aktualizujte analytickou kanál, aby se zobrazily události WCF, které neobsahují žádné chybové události.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="4d0c9-145">Ukázka demonstruje události analytického trasování emitované ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="4d0c9-146">K vyčištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="4d0c9-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="4d0c9-147">Otevřete Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="4d0c9-148">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak na **aplikace-Server-aplikace**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="4d0c9-149">Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **zakázat protokol**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="4d0c9-150">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak na **aplikace-Server-aplikace**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="4d0c9-151">Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **Vymazat protokol**.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="4d0c9-152">Kliknutím na možnost **Vymazat** vymažte události.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d0c9-153">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4d0c9-154">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-154">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="4d0c9-155">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d0c9-156">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4d0c9-156">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="4d0c9-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d0c9-157">See also</span></span>

- [<span data-ttu-id="4d0c9-158">Ukázky monitorování technologie AppFabric</span><span class="sxs-lookup"><span data-stu-id="4d0c9-158">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
