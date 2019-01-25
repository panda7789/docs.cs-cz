---
title: Služby WCF a Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: d45e83919dae52ee3719fe52463711999ba48dd3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555541"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="9af83-102">Služby WCF a Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="9af83-102">WCF Services and Event Tracing for Windows</span></span>
<span data-ttu-id="9af83-103">Tento příklad ukazuje, jak pomocí analytického trasování ve Windows Communication Foundation (WCF) vysílat události do Event Tracing for Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="9af83-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="9af83-104">Analytické trasování jsou události, protože ho na klíčových místech v zásobníku WCF, které umožňují Poradce při potížích pro služby WCF v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="9af83-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="9af83-105">Analytické trasování ve službách WCF je trasování, který je možné zapnout v produkčním prostředí s minimálním dopadem na výkon.</span><span class="sxs-lookup"><span data-stu-id="9af83-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="9af83-106">Trasování jsou emitovány jako události do relace trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="9af83-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="9af83-107">Tato ukázka obsahuje základní služby WCF, ve které události se vysílají ze služby do protokolu událostí, které můžete zobrazit pomocí prohlížeče událostí.</span><span class="sxs-lookup"><span data-stu-id="9af83-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="9af83-108">Také je možné spustit relaci vyhrazené trasování událostí pro Windows, který naslouchá událostem ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="9af83-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="9af83-109">Ukázka zahrnuje skript k vytvoření vyhrazených relace trasování událostí pro Windows, který uchovává události v binárním souboru, který může číst pomocí prohlížeče událostí.</span><span class="sxs-lookup"><span data-stu-id="9af83-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="9af83-110">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="9af83-110">To use this sample</span></span>

1.  <span data-ttu-id="9af83-111">Pomocí sady Visual Studio 2012, otevřete soubor řešení EtwAnalyticTraceSample.sln.</span><span class="sxs-lookup"><span data-stu-id="9af83-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2.  <span data-ttu-id="9af83-112">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="9af83-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="9af83-113">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="9af83-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="9af83-114">Ve webovém prohlížeči, klikněte na tlačítko **Calculator.svc**.</span><span class="sxs-lookup"><span data-stu-id="9af83-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="9af83-115">Identifikátor URI dokumentu WSDL pro službu by se zobrazit v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="9af83-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="9af83-116">Zkopírujte tento identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="9af83-116">Copy that URI.</span></span>

     <span data-ttu-id="9af83-117">Ve výchozím nastavení, služba začne naslouchat požadavkům na portu 1378 `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="9af83-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4.  <span data-ttu-id="9af83-118">Spustíte klienta testu WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="9af83-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="9af83-119">Testovací klient WCF (WcfTestClient.exe) se nachází na `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span><span class="sxs-lookup"><span data-stu-id="9af83-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="9af83-120">Je adresář instalace sady Visual Studio 2012 výchozí `C:\Program Files\Microsoft Visual Studio 10.0`.</span><span class="sxs-lookup"><span data-stu-id="9af83-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5.  <span data-ttu-id="9af83-121">V rámci testovacího klienta WCF, přidání služby tak, že vyberete **souboru**a potom **přidat službu**.</span><span class="sxs-lookup"><span data-stu-id="9af83-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="9af83-122">Přidáte adresu koncového bodu do vstupního pole.</span><span class="sxs-lookup"><span data-stu-id="9af83-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="9af83-123">Výchozí hodnota je `http://localhost:1378/Calculator.svc`.</span><span class="sxs-lookup"><span data-stu-id="9af83-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6.  <span data-ttu-id="9af83-124">Otevřete Prohlížeč událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="9af83-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="9af83-125">Před vyvoláním služby, spusťte Prohlížeč událostí a ujistěte se, že je pro sledování události ze služby WCF, protože ho naslouchání v protokolu událostí.</span><span class="sxs-lookup"><span data-stu-id="9af83-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7.  <span data-ttu-id="9af83-126">Z **Start** nabídce vyberte možnost **nástroje pro správu**a potom **Prohlížeč událostí**.</span><span class="sxs-lookup"><span data-stu-id="9af83-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="9af83-127">Povolit **analytické** a **ladění** protokoly.</span><span class="sxs-lookup"><span data-stu-id="9af83-127">Enable the **Analytic** and **Debug** logs.</span></span>

8.  <span data-ttu-id="9af83-128">Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak **Aplikace Server-**.</span><span class="sxs-lookup"><span data-stu-id="9af83-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="9af83-129">Klikněte pravým tlačítkem na **aplikace Server-** vyberte **zobrazení**a potom **zobrazit protokoly ladění a analýzu**.</span><span class="sxs-lookup"><span data-stu-id="9af83-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="9af83-130">Ujistěte se, **zobrazit protokoly ladění a analýzu** zaškrtnutá možnost.</span><span class="sxs-lookup"><span data-stu-id="9af83-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="9af83-131">Povolit **analytické** protokolu.</span><span class="sxs-lookup"><span data-stu-id="9af83-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="9af83-132">Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak **Aplikace Server-**.</span><span class="sxs-lookup"><span data-stu-id="9af83-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="9af83-133">Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="9af83-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="9af83-134">K otestování služby</span><span class="sxs-lookup"><span data-stu-id="9af83-134">To test the service</span></span>

1.  <span data-ttu-id="9af83-135">Přepněte zpět do klienta testu WCF a dvakrát klikněte na panel `Divide` a ponechte výchozí hodnoty, které určují jmenovatelem 0.</span><span class="sxs-lookup"><span data-stu-id="9af83-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="9af83-136">Je-li jmenovatelem 0, služba vyvolá chybu.</span><span class="sxs-lookup"><span data-stu-id="9af83-136">If the denominator is 0, then the service throws a fault.</span></span>

2.  <span data-ttu-id="9af83-137">Sledujte události generované ze služby.</span><span class="sxs-lookup"><span data-stu-id="9af83-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="9af83-138">Přepněte zpět do prohlížeče událostí a přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak **Aplikace Server-**.</span><span class="sxs-lookup"><span data-stu-id="9af83-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="9af83-139">Klikněte pravým tlačítkem na **analytické** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="9af83-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="9af83-140">Události analytického trasování WCF se zobrazí v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="9af83-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="9af83-141">Zjistíte, že protože způsobil chybu na službu, kterou událost trasování chyby je zobrazena v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="9af83-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3.  <span data-ttu-id="9af83-142">Opakujte kroky 1 a 2, ale s platné vstupy.</span><span class="sxs-lookup"><span data-stu-id="9af83-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="9af83-143">Hodnota `N2` parametr může být cokoli jiného než 0.</span><span class="sxs-lookup"><span data-stu-id="9af83-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="9af83-144">Aktualizovat analytického kanálu zobrazíte WCF událostí neobsahují všechny chybové události.</span><span class="sxs-lookup"><span data-stu-id="9af83-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="9af83-145">Ukázce události analytického trasování ze služby WCF, protože ho.</span><span class="sxs-lookup"><span data-stu-id="9af83-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="9af83-146">Vyčistit (volitelné)</span><span class="sxs-lookup"><span data-stu-id="9af83-146">To cleanup (Optional)</span></span>

1.  <span data-ttu-id="9af83-147">Otevřete Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="9af83-147">Open Event Viewer.</span></span>

2.  <span data-ttu-id="9af83-148">Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru**.</span><span class="sxs-lookup"><span data-stu-id="9af83-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="9af83-149">Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.</span><span class="sxs-lookup"><span data-stu-id="9af83-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3.  <span data-ttu-id="9af83-150">Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru**.</span><span class="sxs-lookup"><span data-stu-id="9af83-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="9af83-151">Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.</span><span class="sxs-lookup"><span data-stu-id="9af83-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4.  <span data-ttu-id="9af83-152">Zvolte **vymazat** možnost pro vymazání událostí.</span><span class="sxs-lookup"><span data-stu-id="9af83-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="9af83-153">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9af83-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9af83-154">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9af83-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9af83-155">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9af83-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9af83-156">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9af83-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="9af83-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9af83-157">See also</span></span>
- [<span data-ttu-id="9af83-158">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="9af83-158">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
