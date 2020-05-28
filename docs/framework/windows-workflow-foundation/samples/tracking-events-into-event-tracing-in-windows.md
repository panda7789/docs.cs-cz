---
title: Sledování událostí ve službě Event Tracking ve Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: fa5d86e327bc9c6eca85ed2908775de5f647f410
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144887"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="f441c-102">Sledování událostí ve službě Event Tracking ve Windows</span><span class="sxs-lookup"><span data-stu-id="f441c-102">Tracking Events into Event Tracing in Windows</span></span>

<span data-ttu-id="f441c-103">Tato ukázka předvádí, jak povolit sledování programovací model Windows Workflow Foundation (WF) ve službě pracovního postupu a jak vygenerovat události sledování v trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="f441c-103">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="f441c-104">K vygenerování záznamů sledování pracovního postupu v ETW používá ukázka účastník sledování ETW ( <xref:System.Activities.Tracking.EtwTrackingParticipant> ).</span><span class="sxs-lookup"><span data-stu-id="f441c-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>

<span data-ttu-id="f441c-105">Pracovní postup v ukázce obdrží požadavek, přiřadí převrácenou vstupní data do vstupní proměnné a vrátí vrácenou zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="f441c-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="f441c-106">Pokud jsou vstupní data 0, dojde k dělení nulou s výjimkou, která je Neošetřená, což způsobí přerušení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="f441c-107">Je-li povoleno sledování, je záznam sledování chyb generován do trasování událostí pro Windows, což může pomoct později vyřešit chybu.</span><span class="sxs-lookup"><span data-stu-id="f441c-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="f441c-108">Účastník sledování ETW je nakonfigurovaný s profilem sledování, aby se mohl přihlásit k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="f441c-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="f441c-109">Profil sledování je definován v souboru Web. config a poskytuje se jako parametr konfigurace účastníkovi sledování ETW.</span><span class="sxs-lookup"><span data-stu-id="f441c-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="f441c-110">Účastník sledování ETW je nakonfigurovaný v souboru Web. config služby pracovního postupu a používá se pro službu jako chování služby.</span><span class="sxs-lookup"><span data-stu-id="f441c-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="f441c-111">V této ukázce zobrazíte události sledování v protokolu událostí pomocí Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="f441c-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>

## <a name="workflow-tracking-details"></a><span data-ttu-id="f441c-112">Podrobnosti sledování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="f441c-112">Workflow Tracking Details</span></span>

<span data-ttu-id="f441c-113">Programovací model Windows Workflow Foundation poskytuje sledovací infrastrukturu pro sledování provádění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-113">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="f441c-114">Modul runtime sledování vytvoří instanci pracovního postupu pro vygenerování událostí souvisejících s životním cyklem pracovního postupu, událostí z aktivit pracovního postupu a vlastními událostmi.</span><span class="sxs-lookup"><span data-stu-id="f441c-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="f441c-115">Následující tabulka podrobně popisuje primární součásti infrastruktury sledování.</span><span class="sxs-lookup"><span data-stu-id="f441c-115">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="f441c-116">Součást</span><span class="sxs-lookup"><span data-stu-id="f441c-116">Component</span></span>|<span data-ttu-id="f441c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f441c-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="f441c-118">Sledování – modul runtime</span><span class="sxs-lookup"><span data-stu-id="f441c-118">Tracking runtime</span></span>|<span data-ttu-id="f441c-119">Poskytuje infrastrukturu pro vygenerování záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="f441c-119">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="f441c-120">Sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="f441c-120">Tracking participants</span></span>|<span data-ttu-id="f441c-121">Přistupuje k záznamům sledování.</span><span class="sxs-lookup"><span data-stu-id="f441c-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="f441c-122">dodává se sledováním účastníka, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="f441c-122">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="f441c-123">Profil sledování</span><span class="sxs-lookup"><span data-stu-id="f441c-123">Tracking profile</span></span>|<span data-ttu-id="f441c-124">Mechanismus filtrování, který umožňuje sledování účastníka přihlásit k odběru podmnožiny sledovacích záznamů emitovaných z instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

<span data-ttu-id="f441c-125">Následující tabulka podrobně popisuje záznamy sledování, které modul runtime pracovního postupu generuje.</span><span class="sxs-lookup"><span data-stu-id="f441c-125">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="f441c-126">Záznam sledování</span><span class="sxs-lookup"><span data-stu-id="f441c-126">Tracking record</span></span>|<span data-ttu-id="f441c-127">Popis</span><span class="sxs-lookup"><span data-stu-id="f441c-127">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="f441c-128">Záznamy sledování instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="f441c-129">Popisuje životní cyklus instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="f441c-130">Například záznam instance je generován při spuštění nebo dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="f441c-131">Záznamy sledování stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="f441c-131">Activity state tracking records.</span></span>|<span data-ttu-id="f441c-132">Podrobnosti provádění aktivity.</span><span class="sxs-lookup"><span data-stu-id="f441c-132">Details activity execution.</span></span> <span data-ttu-id="f441c-133">Tyto záznamy označují stav aktivity pracovního postupu, například když je naplánována aktivita nebo když se aktivita dokončí nebo když je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="f441c-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="f441c-134">Záznam opětovného pokračování záložky</span><span class="sxs-lookup"><span data-stu-id="f441c-134">Bookmark resumption record.</span></span>|<span data-ttu-id="f441c-135">Vygenerováno pokaždé, když je obnovena záložka v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="f441c-136">Vlastní záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="f441c-136">Custom tracking records.</span></span>|<span data-ttu-id="f441c-137">Autor pracovního postupu může vytvořit vlastní záznamy sledování a vygenerovat je v rámci vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="f441c-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="f441c-138">Tento záznam se vygeneruje, když aktivita plánuje jinou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="f441c-138">This record is emitted when an activity schedules another activity.</span></span>|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="f441c-139">Tento záznam je generován při šíření chyby z aktivity.</span><span class="sxs-lookup"><span data-stu-id="f441c-139">This record is emitted when a fault is propagated from an activity.</span></span>|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="f441c-140">Tento záznam se vygeneruje, když se aktivita zruší jinou aktivitou.</span><span class="sxs-lookup"><span data-stu-id="f441c-140">This record is emitted when an activity is canceled by another activity.</span></span>|

<span data-ttu-id="f441c-141">Účastník sledování se přihlásí k odběru podmnožiny vygenerovaných záznamů sledování pomocí sledování profilů.</span><span class="sxs-lookup"><span data-stu-id="f441c-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="f441c-142">Profil sledování obsahuje sledovací dotazy, které umožňují přihlášení k odběru konkrétního typu záznamu sledování.</span><span class="sxs-lookup"><span data-stu-id="f441c-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="f441c-143">Sledování profilů lze zadat v kódu nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f441c-143">Tracking profiles can be specified in code or in configuration.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="f441c-144">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="f441c-144">To use this sample</span></span>

1. <span data-ttu-id="f441c-145">Pomocí sady Visual Studio 2010 otevřete soubor řešení EtwTrackingParticipantSample. sln.</span><span class="sxs-lookup"><span data-stu-id="f441c-145">Using Visual Studio 2010, open the EtwTrackingParticipantSample.sln solution file.</span></span>

2. <span data-ttu-id="f441c-146">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f441c-146">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="f441c-147">Pokud chcete řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="f441c-147">To run the solution, press F5.</span></span>

    <span data-ttu-id="f441c-148">Ve výchozím nastavení naslouchá služba na portu 53797 ( `http://localhost:53797/SampleWorkflowService.xamlx` ).</span><span class="sxs-lookup"><span data-stu-id="f441c-148">By default, the service is listening on port 53797 (`http://localhost:53797/SampleWorkflowService.xamlx`).</span></span>

4. <span data-ttu-id="f441c-149">Pomocí Průzkumníka souborů otevřete testovacího klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="f441c-149">Using File Explorer, open the WCF test client.</span></span>

    <span data-ttu-id="f441c-150">Testovací klient služby WCF (WcfTestClient. exe) se nachází ve \<Visual Studio 2010 installation folder> složce \Common7\IDE\.</span><span class="sxs-lookup"><span data-stu-id="f441c-150">The WCF test client (WcfTestClient.exe) is located in the \<Visual Studio 2010 installation folder>\Common7\IDE\ folder.</span></span>

    <span data-ttu-id="f441c-151">Výchozí instalační složka sady Visual Studio 2010 je C:\Program Files\Microsoft Visual Studio 10,0.</span><span class="sxs-lookup"><span data-stu-id="f441c-151">The default Visual Studio 2010 installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>

5. <span data-ttu-id="f441c-152">V testovacím klientovi WCF vyberte **Přidat službu** z nabídky **soubor** .</span><span class="sxs-lookup"><span data-stu-id="f441c-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>

    <span data-ttu-id="f441c-153">Do vstupního pole přidejte adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="f441c-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="f441c-154">Výchozí formát je `http://localhost:53797/SampleWorkflowService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="f441c-154">The default is `http://localhost:53797/SampleWorkflowService.xamlx`.</span></span>

6. <span data-ttu-id="f441c-155">Otevřete aplikaci Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="f441c-155">Open the Event Viewer application.</span></span>

    <span data-ttu-id="f441c-156">Před vyvoláním služby spusťte Prohlížeč událostí v nabídce **Start** vyberte **Spustit** a zadejte `eventvwr.exe` .</span><span class="sxs-lookup"><span data-stu-id="f441c-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="f441c-157">Zajistěte, aby protokol událostí naslouchal sledování událostí vydaných ze služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>

7. <span data-ttu-id="f441c-158">Ve stromovém zobrazení Prohlížeč událostí přejděte do části **Prohlížeč událostí**, **protokoly aplikací a služeb**a **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="f441c-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="f441c-159">Klikněte pravým tlačítkem myši na **Microsoft** a vyberte **Zobrazit** a pak **Zobrazte protokoly o analýze a ladění** , aby se aktivovaly protokoly pro analýzu a ladění.</span><span class="sxs-lookup"><span data-stu-id="f441c-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>

    <span data-ttu-id="f441c-160">Zajistěte, aby byla zaškrtnuta možnost **Zobrazit protokoly o analýze a ladění** .</span><span class="sxs-lookup"><span data-stu-id="f441c-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

8. <span data-ttu-id="f441c-161">Ve stromovém zobrazení v Prohlížeč událostí přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f441c-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="f441c-162">Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol** pro povolení **analytického** protokolu.</span><span class="sxs-lookup"><span data-stu-id="f441c-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>

9. <span data-ttu-id="f441c-163">Otestujte službu pomocí testovacího klienta WCF dvojitým kliknutím `GetData` .</span><span class="sxs-lookup"><span data-stu-id="f441c-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>

    <span data-ttu-id="f441c-164">Tím se otevře `GetData` metoda.</span><span class="sxs-lookup"><span data-stu-id="f441c-164">This opens the `GetData` method.</span></span> <span data-ttu-id="f441c-165">Požadavek akceptuje jeden parametr a zajistí, že hodnota je 0, což je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="f441c-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>

     <span data-ttu-id="f441c-166">Klikněte na **vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="f441c-166">Click **Invoke**.</span></span>

10. <span data-ttu-id="f441c-167">Sledujte události vydávané z pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-167">Observe the events emitted from the workflow.</span></span>

    <span data-ttu-id="f441c-168">Přepněte zpět na Prohlížeč událostí a přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f441c-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="f441c-169">Klikněte pravým tlačítkem na možnost **analytické** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="f441c-169">Right-click **Analytic** and select **Refresh**.</span></span>

    <span data-ttu-id="f441c-170">Události pracovního postupu se zobrazí v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="f441c-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="f441c-171">Všimněte si, že se zobrazují události spuštění pracovního postupu a že jeden z nich je Neošetřená výjimka, která odpovídá chybě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="f441c-172">Kromě toho je vyvolána událost upozornění z aktivity pracovního postupu, která indikuje, že aktivita vyvolává chybu.</span><span class="sxs-lookup"><span data-stu-id="f441c-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>

11. <span data-ttu-id="f441c-173">Opakujte kroky 9 a 10 se vstupem dat s výjimkou 0, aby nedošlo k žádné chybě.</span><span class="sxs-lookup"><span data-stu-id="f441c-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>

<span data-ttu-id="f441c-174">Sledování profilů vám umožní přihlásit se k odběru událostí vygenerovaných modulem runtime při změně stavu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="f441c-175">V závislosti na požadavcích na monitorování můžete vytvořit profil, který je velmi hrubý, který se přihlásí k odběru malé sady změn stavu vysoké úrovně v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="f441c-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="f441c-176">Na druhé straně můžete vytvořit velmi přesný profil, jehož výstup bude dostatečně bohatý, aby bylo možné provést pozdější opětovné vytvoření provádění.</span><span class="sxs-lookup"><span data-stu-id="f441c-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="f441c-177">Ukázka demonstruje události emitované z modulu runtime pracovního postupu do ETW pomocí nástroje `HealthMonitoring Tracking Profile` , který generuje malou sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="f441c-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="f441c-178">Jiný profil, který generuje další události sledování pracovního postupu, je k dispozici také v souboru Web. config, který je pojmenován `Troubleshooting Tracking Profile` .</span><span class="sxs-lookup"><span data-stu-id="f441c-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="f441c-179">Při [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] instalaci nástroje je v souboru Machine. config nakonfigurován výchozí profil s prázdným názvem.</span><span class="sxs-lookup"><span data-stu-id="f441c-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="f441c-180">Tento profil se používá v konfiguraci chování sledování trasování událostí pro Windows, pokud není zadaný název profilu ani název prázdného profilu.</span><span class="sxs-lookup"><span data-stu-id="f441c-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>

<span data-ttu-id="f441c-181">Profil sledování stavu vygeneruje záznamy instancí pracovního postupu a záznamy šíření chyb aktivity.</span><span class="sxs-lookup"><span data-stu-id="f441c-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="f441c-182">Tento profil je vytvořen přidáním následujícího profilu sledování do konfiguračního souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="f441c-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>

```xml
<tracking>
  <profiles>
    <trackingProfile name="HealthMonitoring Tracking Profile">
      <workflow activityDefinitionId="*">
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Started"/>
              <state name="Completed"/>
              <state name="Aborted"/>
              <state name="UnhandledException"/>
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```

 <span data-ttu-id="f441c-183">Profil se dá změnit tak, že změníte `EtwTrackingParticipant` konfiguraci na následující.</span><span class="sxs-lookup"><span data-stu-id="f441c-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <etwTracking profileName="HealthMonitoring Tracking Profile"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

#### <a name="to-clean-up-optional"></a><span data-ttu-id="f441c-184">Vyčištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="f441c-184">To clean up (Optional)</span></span>

1. <span data-ttu-id="f441c-185">Otevřete Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="f441c-185">Open Event Viewer.</span></span>

2. <span data-ttu-id="f441c-186">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f441c-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="f441c-187">Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **zakázat protokol**.</span><span class="sxs-lookup"><span data-stu-id="f441c-187">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="f441c-188">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f441c-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="f441c-189">Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **Vymazat protokol**.</span><span class="sxs-lookup"><span data-stu-id="f441c-189">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="f441c-190">Kliknutím na možnost **Vymazat** vymažte události.</span><span class="sxs-lookup"><span data-stu-id="f441c-190">Choose the **Clear** option to clear the events.</span></span>

## <a name="known-issue"></a><span data-ttu-id="f441c-191">Známý problém</span><span class="sxs-lookup"><span data-stu-id="f441c-191">Known Issue</span></span>

> [!NOTE]
> <span data-ttu-id="f441c-192">Došlo k známému problému Prohlížeč událostí, kde se nemusí podařit dekódovat události ETW.</span><span class="sxs-lookup"><span data-stu-id="f441c-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="f441c-193">Může se zobrazit chybová zpráva, která vypadá nějak takto:</span><span class="sxs-lookup"><span data-stu-id="f441c-193">You may see an error message that looks like the following.</span></span>
>
> <span data-ttu-id="f441c-194">Popis ID události \<id> ze zdrojového serveru Microsoft-Windows-Application Server nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="f441c-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="f441c-195">Buď není v místním počítači nainstalována komponenta, která vyvolává tuto událost, nebo je instalace poškozena.</span><span class="sxs-lookup"><span data-stu-id="f441c-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="f441c-196">Součást můžete nainstalovat nebo opravit v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="f441c-196">You can install or repair the component on the local computer.</span></span>
>
> <span data-ttu-id="f441c-197">Pokud k této chybě dojde, klikněte v podokně akce na aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="f441c-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="f441c-198">Událost by se teď měla dekódovat správně.</span><span class="sxs-lookup"><span data-stu-id="f441c-198">The event should now decode properly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f441c-199">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="f441c-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f441c-200">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f441c-200">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f441c-201">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="f441c-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f441c-202">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f441c-202">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`

## <a name="see-also"></a><span data-ttu-id="f441c-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="f441c-203">See also</span></span>

- <span data-ttu-id="f441c-204">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="f441c-204">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
