---
title: Služby WCF a Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183202"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="6c862-102">Služby WCF a Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="6c862-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="6c862-103">Tato ukázka ukazuje, jak použít analytické trasování v Systému Windows Communication Foundation (WCF) k vyzařování událostí v trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="6c862-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="6c862-104">Analytické trasování jsou události vyzařované v klíčových bodech v zásobníku WCF, které umožňují řešení potíží se službami WCF v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="6c862-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="6c862-105">Analytické trasování ve službách WCF je trasování, které lze zapnout v produkčním prostředí s minimálním dopadem na výkon.</span><span class="sxs-lookup"><span data-stu-id="6c862-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="6c862-106">Tyto trasování jsou vydávány jako události relace ETW.</span><span class="sxs-lookup"><span data-stu-id="6c862-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="6c862-107">Tato ukázka zahrnuje základní službu WCF, ve které jsou události vyzařovány ze služby do protokolu událostí, které lze zobrazit pomocí Prohlížeče událostí.</span><span class="sxs-lookup"><span data-stu-id="6c862-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="6c862-108">Je také možné spustit vyhrazené relace ETW, který naslouchá události ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6c862-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="6c862-109">Ukázka obsahuje skript pro vytvoření vyhrazené relace ETW, která ukládá události v binárním souboru, který lze číst pomocí Prohlížeče událostí.</span><span class="sxs-lookup"><span data-stu-id="6c862-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="6c862-110">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="6c862-110">To use this sample</span></span>

1. <span data-ttu-id="6c862-111">Pomocí Visual Studia 2012 otevřete soubor řešení EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="6c862-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="6c862-112">Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="6c862-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="6c862-113">Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="6c862-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="6c862-114">Ve webovém prohlížeči klepněte na položku **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="6c862-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="6c862-115">Identifikátor URI dokumentu WSDL pro službu by se měl zobrazit v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="6c862-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="6c862-116">Zkopírujte tento identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="6c862-116">Copy that URI.</span></span>

     <span data-ttu-id="6c862-117">Ve výchozím nastavení služba spustí naslouchání požadavkům `http://localhost:1378/Calculator.svc`na portu 1378 .</span><span class="sxs-lookup"><span data-stu-id="6c862-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="6c862-118">Spusťte testovacího klienta WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="6c862-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="6c862-119">Testovací klient WCF (WcfTestClient.exe) `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`je umístěn na adrese .</span><span class="sxs-lookup"><span data-stu-id="6c862-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="6c862-120">Výchozí instalační dir sady Visual Studio `C:\Program Files\Microsoft Visual Studio 10.0`2012 je .</span><span class="sxs-lookup"><span data-stu-id="6c862-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="6c862-121">V rámci testovacího klienta WCF přidejte službu výběrem **položky Soubor**a potom **přidejte službu**.</span><span class="sxs-lookup"><span data-stu-id="6c862-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="6c862-122">Přidejte adresu koncového bodu do vstupního pole.</span><span class="sxs-lookup"><span data-stu-id="6c862-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="6c862-123">Výchozí formát je `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="6c862-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="6c862-124">Otevřete aplikaci Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="6c862-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="6c862-125">Před vyvoláním služby spusťte Prohlížeč událostí a ujistěte se, že protokol událostí naslouchá sledování událostí vyzařovaných ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6c862-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="6c862-126">V nabídce **Start** vyberte **Nástroje pro správu**a potom **prohlížeč událostí**.</span><span class="sxs-lookup"><span data-stu-id="6c862-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="6c862-127">Povolte protokoly **Analytic a** **Ladění.**</span><span class="sxs-lookup"><span data-stu-id="6c862-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="6c862-128">Ve stromovém zobrazení v Prohlížeči událostí přejděte do **prohlížeče událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikace aplikačního serveru**.</span><span class="sxs-lookup"><span data-stu-id="6c862-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="6c862-129">Klepněte pravým tlačítkem myši na **položku Aplikační server-Aplikace**, vyberte příkaz **Zobrazit**a potom **zobrazit protokoly analýzy a ladění**.</span><span class="sxs-lookup"><span data-stu-id="6c862-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="6c862-130">Ujistěte se, že je zaškrtnuta možnost **Zobrazit protokoly analýzy a ladění.**</span><span class="sxs-lookup"><span data-stu-id="6c862-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="6c862-131">Povolte protokol **Analytická.**</span><span class="sxs-lookup"><span data-stu-id="6c862-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="6c862-132">Ve stromovém zobrazení v Prohlížeči událostí přejděte do **prohlížeče událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikace aplikačního serveru**.</span><span class="sxs-lookup"><span data-stu-id="6c862-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="6c862-133">Klepněte pravým tlačítkem myši na **službu Analytick** a vyberte **příkaz Povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="6c862-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="6c862-134">Chcete-li otestovat službu</span><span class="sxs-lookup"><span data-stu-id="6c862-134">To test the service</span></span>

1. <span data-ttu-id="6c862-135">Přepněte zpět do testovacího klienta WCF a poklepejte na `Divide` výchozí hodnoty, které určují jmenovatel 0.</span><span class="sxs-lookup"><span data-stu-id="6c862-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="6c862-136">Pokud je jmenovatel 0, pak služba vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="6c862-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="6c862-137">Sledujte události vyzařované ze služby.</span><span class="sxs-lookup"><span data-stu-id="6c862-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="6c862-138">Přepněte zpět do Prohlížeče událostí a přejděte do **prohlížeče událostí**, **protokolů aplikací a služeb**, společnosti **Microsoft**, **Systému Windows**a **následných aplikací aplikačního serveru**.</span><span class="sxs-lookup"><span data-stu-id="6c862-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="6c862-139">Klikněte pravým tlačítkem myši na **Službu Analyticka** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="6c862-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="6c862-140">V prohlížeči událostí jsou zobrazeny události analytického trasování WCF.</span><span class="sxs-lookup"><span data-stu-id="6c862-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="6c862-141">Všimněte si, že vzhledem k tomu, že služba vyvolala chybu, zobrazí se v prohlížeči událostí událost sledování chyb.</span><span class="sxs-lookup"><span data-stu-id="6c862-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="6c862-142">Opakujte kroky 1 a 2, ale s platnými vstupy.</span><span class="sxs-lookup"><span data-stu-id="6c862-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="6c862-143">Hodnota parametru `N2` může být libovolné číslo než 0.</span><span class="sxs-lookup"><span data-stu-id="6c862-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="6c862-144">Aktualizujte analytický kanál pro zobrazení událostí WCF neobsahují žádné chybové události.</span><span class="sxs-lookup"><span data-stu-id="6c862-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="6c862-145">Ukázka ukazuje události trasování analytická vyzařované ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="6c862-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="6c862-146">Vyčištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="6c862-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="6c862-147">Otevřete Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="6c862-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="6c862-148">Přejděte do **prohlížeče událostí**, **protokolů aplikací a služeb**, společnosti **Microsoft**, **Systému Windows**a **následných aplikací aplikačního serveru**.</span><span class="sxs-lookup"><span data-stu-id="6c862-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="6c862-149">Klepněte pravým tlačítkem myši na **službu Analytická** a vyberte **příkaz Zakázat protokol**.</span><span class="sxs-lookup"><span data-stu-id="6c862-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="6c862-150">Přejděte do **prohlížeče událostí**, **protokolů aplikací a služeb**, společnosti **Microsoft**, **Systému Windows**a **následných aplikací aplikačního serveru**.</span><span class="sxs-lookup"><span data-stu-id="6c862-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="6c862-151">Klepněte pravým tlačítkem myši na **položku Analytická** a vyberte příkaz **Vymazat protokol**.</span><span class="sxs-lookup"><span data-stu-id="6c862-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="6c862-152">Zvolte možnost **Vymazat,** chcete-li události vymazat.</span><span class="sxs-lookup"><span data-stu-id="6c862-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6c862-153">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="6c862-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6c862-154">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="6c862-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6c862-155">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6c862-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c862-156">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c862-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="6c862-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c862-157">See also</span></span>

- <span data-ttu-id="6c862-158">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6c862-158">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
