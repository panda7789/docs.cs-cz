---
title: "Služby WCF a Trasování událostí pro Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cb8924cc04442e3b9eda5e251e6dcdc57f5660c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="1b8f5-102">Služby WCF a Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="1b8f5-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="1b8f5-103">Tento příklad ukazuje, jak použít analytické trasování v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pro vydávání událostí v události trasování pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="1b8f5-103">This sample demonstrates how to use the analytic tracing in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="1b8f5-104">Analytické trasování jsou události vygenerované v klíčové body [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zásobníku, který umožní řešení potíží s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-104">The analytic traces are events emitted at key points in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stack that allow troubleshooting of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services in production environment.</span></span>  
  
 <span data-ttu-id="1b8f5-105">Analytické trasování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services je trasování, který lze zapnout v produkčním prostředí s minimálním dopadem na výkon.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-105">Analytic trace in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="1b8f5-106">Toto trasování jsou vydávány jako události relaci trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-106">These traces are emitted as events to an ETW session.</span></span>  
  
 <span data-ttu-id="1b8f5-107">Tato ukázka obsahuje základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v události, které jsou vygenerované ze služby do protokolu událostí, který lze zobrazit pomocí prohlížeče událostí.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-107">This sample includes a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="1b8f5-108">Je také možné spustit relaci vyhrazené trasování událostí pro Windows, která naslouchá událostem z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-108">It is also possible to start a dedicated ETW session that listens for events from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="1b8f5-109">Ukázka zahrnuje skript pro vytvoření vyhrazené relace trasování událostí pro Windows, která ukládá události v binární soubor, který lze číst pomocí prohlížeče událostí.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1b8f5-110">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="1b8f5-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="1b8f5-111">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the EtwAnalyticTraceSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="1b8f5-112">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1b8f5-113">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-113">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="1b8f5-114">Ve webovém prohlížeči, klikněte na tlačítko **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="1b8f5-115">Identifikátor URI dokumentu WSDL služby by se zobrazit v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="1b8f5-116">Zkopírujte tento identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-116">Copy that URI.</span></span>  
  
     <span data-ttu-id="1b8f5-117">Ve výchozím nastavení spustí službu naslouchání požadavkům na portu 1378 (http://localhost:1378/Calculator.svc).</span><span class="sxs-lookup"><span data-stu-id="1b8f5-117">By default, the service starts listening for requests on port 1378 (http://localhost:1378/Calculator.svc).</span></span>  
  
4.  <span data-ttu-id="1b8f5-118">Spustit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] testovacího klienta (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="1b8f5-118">Run the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="1b8f5-119">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Testovacího klienta (WcfTestClient.exe) se nachází v \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] nainstalovat Dir > \Common7\IDE\ WcfTestClient.exe (výchozí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir instalace je C:\Program Files\Microsoft Visual Studio 10.0).</span><span class="sxs-lookup"><span data-stu-id="1b8f5-119">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="1b8f5-120">V rámci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] testování klienta, přidejte službu tak, že vyberete **soubor**a potom **přidat službu**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-120">Within the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="1b8f5-121">Přidáte adresa koncového bodu do vstupního pole.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-121">Add the endpoint address in the input box.</span></span> <span data-ttu-id="1b8f5-122">Výchozí hodnota je http://localhost:1378/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-122">The default is http://localhost:1378/Calculator.svc.</span></span>  
  
6.  <span data-ttu-id="1b8f5-123">Otevřete Prohlížeč událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-123">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="1b8f5-124">Před vyvoláním služby, spusťte Prohlížeč událostí a zkontrolujte, zda protokol událostí naslouchá pro sledování události vygenerované ze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-124">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
7.  <span data-ttu-id="1b8f5-125">Z **spustit** nabídce vyberte možnost **nástroje pro správu**a potom **Prohlížeč událostí**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-125">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="1b8f5-126">Povolit **analytické** a **ladění** protokoly.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-126">Enable the **Analytic** and **Debug** logs.</span></span>  
  
8.  <span data-ttu-id="1b8f5-127">Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom **Serveru aplikace – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-127">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="1b8f5-128">Klikněte pravým tlačítkem na **serveru aplikace – aplikace**, vyberte **zobrazení**a potom **zobrazit protokoly pro ladění a**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-128">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="1b8f5-129">Ujistěte se, že **zobrazit protokoly pro ladění a** zaškrtnutá možnost.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-129">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>  
  
9. <span data-ttu-id="1b8f5-130">Povolit **analytické** protokolu.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-130">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="1b8f5-131">Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom **Serveru aplikace – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-131">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="1b8f5-132">Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-132">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
#### <a name="to-test-the-service"></a><span data-ttu-id="1b8f5-133">K testování služby</span><span class="sxs-lookup"><span data-stu-id="1b8f5-133">To test the service</span></span>  
  
1.  <span data-ttu-id="1b8f5-134">Přepněte zpět na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] testování klienta a dvakrát klikněte na `Divide` a ponechte výchozí hodnoty, které určují jmenovatel 0.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-134">Switch back to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>  
  
     <span data-ttu-id="1b8f5-135">Pokud jmenovatel hodnotu 0, služba vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-135">If the denominator is 0, then the service throws a fault.</span></span>  
  
2.  <span data-ttu-id="1b8f5-136">Pozorovat, jaké události vygenerované ze služby.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-136">Observe the events emitted from the service.</span></span>  
  
     <span data-ttu-id="1b8f5-137">Přepněte zpět do prohlížeče událostí a přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom **Serveru aplikace – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-137">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="1b8f5-138">Klikněte pravým tlačítkem na **analytické** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-138">Right-click **Analytic** and select **Refresh**.</span></span>  
  
     <span data-ttu-id="1b8f5-139">Události analytického trasování WCF se zobrazí v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-139">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="1b8f5-140">Zjistíte, že vzhledem k tomu, že byl vyvolané chybu služby, kterou chybovou událost trasování je zobrazena události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-140">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>  
  
3.  <span data-ttu-id="1b8f5-141">Opakujte kroky 1 a 2, ale s platné vstupní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-141">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="1b8f5-142">Hodnota `N2` parametr může být číslo než 0.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-142">The value of the `N2` parameter can be any number other than 0.</span></span>  
  
     <span data-ttu-id="1b8f5-143">Aktualizujte analytické kanál zobrazíte WCF události nezahrnují všechny chybové události.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-143">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>  
  
 <span data-ttu-id="1b8f5-144">Ukázka ukazuje analytického trasování události vygenerované ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-144">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="1b8f5-145">Pro čištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="1b8f5-145">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="1b8f5-146">Otevřete Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-146">Open Event Viewer.</span></span>  
  
2.  <span data-ttu-id="1b8f5-147">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru aplikace**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-147">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="1b8f5-148">Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-148">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="1b8f5-149">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru aplikace**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-149">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="1b8f5-150">Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-150">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="1b8f5-151">Vyberte **vymazat** možnost Vymazat události.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-151">Choose the **Clear** option to clear the events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1b8f5-152">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-152">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1b8f5-153">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="1b8f5-153">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1b8f5-154">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1b8f5-155">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="1b8f5-155">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="1b8f5-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b8f5-156">See Also</span></span>  
 [<span data-ttu-id="1b8f5-157">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="1b8f5-157">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
