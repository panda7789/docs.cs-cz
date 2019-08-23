---
title: Sledování událostí ve službě Event Tracking ve Windows
ms.date: 03/30/2017
ms.assetid: f812659b-0943-45ff-9430-4defa733182b
ms.openlocfilehash: 48ffbbb8ccac34c5eb605edc4aab17d0e2b3499e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922927"
---
# <a name="tracking-events-into-event-tracing-in-windows"></a><span data-ttu-id="77e57-102">Sledování událostí ve službě Event Tracking ve Windows</span><span class="sxs-lookup"><span data-stu-id="77e57-102">Tracking Events into Event Tracing in Windows</span></span>
<span data-ttu-id="77e57-103">Tato ukázka předvádí, jak povolit sledování programovací model Windows Workflow Foundation (WF) ve službě pracovního postupu a jak vygenerovat události sledování v trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="77e57-103">This sample demonstrates how to enable Windows Workflow Foundation (WF) tracking on a workflow service and emit the tracking events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="77e57-104">K vygenerování záznamů sledování pracovního postupu v ETW používá ukázka účastník sledování ETW (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span><span class="sxs-lookup"><span data-stu-id="77e57-104">To emit workflow tracking records into ETW, the sample uses the ETW tracking participant (<xref:System.Activities.Tracking.EtwTrackingParticipant>).</span></span>

 <span data-ttu-id="77e57-105">Pracovní postup v ukázce obdrží požadavek, přiřadí převrácenou vstupní data do vstupní proměnné a vrátí vrácenou zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="77e57-105">The workflow in the sample receives a request, assigns the reciprocal of the input data to the input variable and returns the reciprocal back to the client.</span></span> <span data-ttu-id="77e57-106">Pokud jsou vstupní data 0, dojde k dělení nulou s výjimkou, která je Neošetřená, což způsobí přerušení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-106">When the input data is 0, a divide by zero exception occurs that is unhandled that causes the workflow to abort.</span></span> <span data-ttu-id="77e57-107">Je-li povoleno sledování, je záznam sledování chyb generován do trasování událostí pro Windows, což může pomoct později vyřešit chybu.</span><span class="sxs-lookup"><span data-stu-id="77e57-107">With tracking enabled, the error track record is emitted to ETW, which can help troubleshoot the error later.</span></span> <span data-ttu-id="77e57-108">Účastník sledování ETW je nakonfigurovaný s profilem sledování, aby se mohl přihlásit k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="77e57-108">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="77e57-109">Profil sledování je definován v souboru Web. config a poskytuje se jako parametr konfigurace účastníkovi sledování ETW.</span><span class="sxs-lookup"><span data-stu-id="77e57-109">The tracking profile is defined in the Web.config file and provided as a configuration parameter to the ETW tracking participant.</span></span> <span data-ttu-id="77e57-110">Účastník sledování ETW je nakonfigurovaný v souboru Web. config služby pracovního postupu a používá se pro službu jako chování služby.</span><span class="sxs-lookup"><span data-stu-id="77e57-110">The ETW tracking participant is configured in the Web.config file of the workflow service and is applied to the service as a service behavior.</span></span> <span data-ttu-id="77e57-111">V této ukázce zobrazíte události sledování v protokolu událostí pomocí Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="77e57-111">In this sample, you view the tracking events in the event log using Event Viewer.</span></span>

## <a name="workflow-tracking-details"></a><span data-ttu-id="77e57-112">Podrobnosti sledování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="77e57-112">Workflow Tracking Details</span></span>
 <span data-ttu-id="77e57-113">Programovací model Windows Workflow Foundation poskytuje sledovací infrastrukturu pro sledování provádění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-113">Windows Workflow Foundation provides a tracking infrastructure to track the execution of a workflow instance.</span></span> <span data-ttu-id="77e57-114">Modul runtime sledování vytvoří instanci pracovního postupu pro vygenerování událostí souvisejících s životním cyklem pracovního postupu, událostí z aktivit pracovního postupu a vlastními událostmi.</span><span class="sxs-lookup"><span data-stu-id="77e57-114">The tracking runtime creates a workflow instance to emit events related to the workflow lifecycle, events from workflow activities and custom events.</span></span> <span data-ttu-id="77e57-115">Následující tabulka podrobně popisuje primární součásti infrastruktury sledování.</span><span class="sxs-lookup"><span data-stu-id="77e57-115">The following table details the primary components of the tracking infrastructure.</span></span>

|<span data-ttu-id="77e57-116">Součást</span><span class="sxs-lookup"><span data-stu-id="77e57-116">Component</span></span>|<span data-ttu-id="77e57-117">Popis</span><span class="sxs-lookup"><span data-stu-id="77e57-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="77e57-118">Sledování – modul runtime</span><span class="sxs-lookup"><span data-stu-id="77e57-118">Tracking runtime</span></span>|<span data-ttu-id="77e57-119">Poskytuje infrastrukturu pro vygenerování záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="77e57-119">Provides the infrastructure to emit tracking records.</span></span>|
|<span data-ttu-id="77e57-120">Sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="77e57-120">Tracking participants</span></span>|<span data-ttu-id="77e57-121">Přistupuje k záznamům sledování.</span><span class="sxs-lookup"><span data-stu-id="77e57-121">Accesses the tracking records.</span></span> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]<span data-ttu-id="77e57-122">dodává se sledováním účastníka, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="77e57-122">ships with a tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span>|
|<span data-ttu-id="77e57-123">Profil sledování</span><span class="sxs-lookup"><span data-stu-id="77e57-123">Tracking profile</span></span>|<span data-ttu-id="77e57-124">Mechanismus filtrování, který umožňuje sledování účastníka přihlásit k odběru podmnožiny sledovacích záznamů emitovaných z instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-124">A filtering mechanism that allows a tracking participant to subscribe for a subset of the tracking records emitted from a workflow instance.</span></span>|

 <span data-ttu-id="77e57-125">Následující tabulka podrobně popisuje záznamy sledování, které modul runtime pracovního postupu generuje.</span><span class="sxs-lookup"><span data-stu-id="77e57-125">The following table details the tracking records that the workflow runtime emits.</span></span>

|<span data-ttu-id="77e57-126">Záznam sledování</span><span class="sxs-lookup"><span data-stu-id="77e57-126">Tracking record</span></span>|<span data-ttu-id="77e57-127">Popis</span><span class="sxs-lookup"><span data-stu-id="77e57-127">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="77e57-128">Záznamy sledování instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-128">Workflow instance tracking records.</span></span>|<span data-ttu-id="77e57-129">Popisuje životní cyklus instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-129">Describes the lifecycle of the workflow instance.</span></span> <span data-ttu-id="77e57-130">Například záznam instance je generován při spuštění nebo dokončení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-130">For example, an instance record is emitted when the workflow starts or completes.</span></span>|
|<span data-ttu-id="77e57-131">Záznamy sledování stavu aktivity.</span><span class="sxs-lookup"><span data-stu-id="77e57-131">Activity state tracking records.</span></span>|<span data-ttu-id="77e57-132">Podrobnosti provádění aktivity.</span><span class="sxs-lookup"><span data-stu-id="77e57-132">Details activity execution.</span></span> <span data-ttu-id="77e57-133">Tyto záznamy označují stav aktivity pracovního postupu, například když je naplánována aktivita nebo když se aktivita dokončí nebo když je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="77e57-133">These records indicate the state of a workflow activity such as when an activity is scheduled or when the activity completes or when a fault is thrown.</span></span>|
|<span data-ttu-id="77e57-134">Záznam opětovného pokračování záložky</span><span class="sxs-lookup"><span data-stu-id="77e57-134">Bookmark resumption record.</span></span>|<span data-ttu-id="77e57-135">Vygenerováno pokaždé, když je obnovena záložka v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-135">Emitted whenever a bookmark within a workflow instance is resumed.</span></span>|
|<span data-ttu-id="77e57-136">Vlastní záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="77e57-136">Custom tracking records.</span></span>|<span data-ttu-id="77e57-137">Autor pracovního postupu může vytvořit vlastní záznamy sledování a vygenerovat je v rámci vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="77e57-137">A workflow author can create custom tracking records and emit them within the custom activity.</span></span>|
|<xref:System.Activities.Tracking.ActivityScheduledRecord>|<span data-ttu-id="77e57-138">Tento záznam se vygeneruje, když aktivita plánuje jinou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="77e57-138">This record is emitted when an activity schedules another activity.</span></span>|
|<xref:System.Activities.Tracking.FaultPropagationRecord>|<span data-ttu-id="77e57-139">Tento záznam je generován při šíření chyby z aktivity.</span><span class="sxs-lookup"><span data-stu-id="77e57-139">This record is emitted when a fault is propagated from an activity.</span></span>|
|<xref:System.Activities.Tracking.CancelRequestedRecord>|<span data-ttu-id="77e57-140">Tento záznam se vygeneruje, když se aktivita zruší jinou aktivitou.</span><span class="sxs-lookup"><span data-stu-id="77e57-140">This record is emitted when an activity is canceled by another activity.</span></span>|

 <span data-ttu-id="77e57-141">Účastník sledování se přihlásí k odběru podmnožiny vygenerovaných záznamů sledování pomocí sledování profilů.</span><span class="sxs-lookup"><span data-stu-id="77e57-141">The tracking participant subscribes for a subset of the emitted tracking records using tracking profiles.</span></span> <span data-ttu-id="77e57-142">Profil sledování obsahuje sledovací dotazy, které umožňují přihlášení k odběru konkrétního typu záznamu sledování.</span><span class="sxs-lookup"><span data-stu-id="77e57-142">A tracking profile contains tracking queries that allow subscribing for a particular tracking record type.</span></span> <span data-ttu-id="77e57-143">Sledování profilů lze zadat v kódu nebo v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="77e57-143">Tracking profiles can be specified in code or in configuration.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="77e57-144">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="77e57-144">To use this sample</span></span>

1. <span data-ttu-id="77e57-145">Pomocí sady Visual Studio 2010 otevřete soubor řešení EtwTrackingParticipantSample. sln.</span><span class="sxs-lookup"><span data-stu-id="77e57-145">Using Visual Studio 2010, open the EtwTrackingParticipantSample.sln solution file.</span></span>

2. <span data-ttu-id="77e57-146">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="77e57-146">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="77e57-147">Pokud chcete řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="77e57-147">To run the solution, press F5.</span></span>

     <span data-ttu-id="77e57-148">Ve výchozím nastavení naslouchá služba na portu 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span><span class="sxs-lookup"><span data-stu-id="77e57-148">By default, the service is listening on port 53797 (http://localhost:53797/SampleWorkflowService.xamlx).</span></span>

4. <span data-ttu-id="77e57-149">Pomocí Průzkumníka souborů otevřete testovacího klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="77e57-149">Using File Explorer, open the WCF test client.</span></span>

     <span data-ttu-id="77e57-150">Testovací klient služby WCF (WcfTestClient. exe) se nachází v instalační \<složce sady Visual Studio 2010 > složce \Common7\IDE\.</span><span class="sxs-lookup"><span data-stu-id="77e57-150">The WCF test client (WcfTestClient.exe) is located in the \<Visual Studio 2010 installation folder>\Common7\IDE\ folder.</span></span>

     <span data-ttu-id="77e57-151">Výchozí instalační složka sady Visual Studio 2010 je C:\Program Files\Microsoft Visual Studio 10,0.</span><span class="sxs-lookup"><span data-stu-id="77e57-151">The default Visual Studio 2010 installation folder is C:\Program Files\Microsoft Visual Studio 10.0.</span></span>

5. <span data-ttu-id="77e57-152">V testovacím klientovi WCF vyberte **Přidat službu** z nabídky **soubor** .</span><span class="sxs-lookup"><span data-stu-id="77e57-152">In WCF test client, select **Add Service** from the **File** menu.</span></span>

     <span data-ttu-id="77e57-153">Do vstupního pole přidejte adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="77e57-153">Add the endpoint address in the input box.</span></span> <span data-ttu-id="77e57-154">Výchozí hodnota je `http://localhost:53797/SampleWorkflowService.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="77e57-154">The default is `http://localhost:53797/SampleWorkflowService.xamlx`.</span></span>

6. <span data-ttu-id="77e57-155">Otevřete Prohlížeč událostí aplikace.</span><span class="sxs-lookup"><span data-stu-id="77e57-155">Open the Event Viewer application.</span></span>

     <span data-ttu-id="77e57-156">Před vyvoláním služby spusťte Prohlížeč událostí v nabídce **Start** vyberte **Spustit** `eventvwr.exe`a zadejte.</span><span class="sxs-lookup"><span data-stu-id="77e57-156">Before invoking the service, start Event Viewer from the **Start** menu, select **Run** and type in `eventvwr.exe`.</span></span> <span data-ttu-id="77e57-157">Zajistěte, aby protokol událostí naslouchal sledování událostí vydaných ze služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-157">Ensure that the event log is listening for tracking events emitted from the workflow service.</span></span>

7. <span data-ttu-id="77e57-158">Ve stromovém zobrazení Prohlížeč událostí přejděte do části **Prohlížeč událostí**, **protokoly aplikací a služeb**a **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="77e57-158">In the tree view of the Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, and **Microsoft**.</span></span> <span data-ttu-id="77e57-159">Klikněte pravým tlačítkem myši na **Microsoft** a vyberte **Zobrazit** a pak **Zobrazte protokoly o analýze a ladění** , aby se aktivovaly protokoly pro analýzu a ladění.</span><span class="sxs-lookup"><span data-stu-id="77e57-159">Right-click **Microsoft** and select **View** and then **Show Analytic and Debug Logs** to enable the analytic and debug logs</span></span>

     <span data-ttu-id="77e57-160">Zajistěte, aby byla zaškrtnuta možnost **Zobrazit protokoly o analýze a ladění** .</span><span class="sxs-lookup"><span data-stu-id="77e57-160">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

8. <span data-ttu-id="77e57-161">Ve stromovém zobrazení v Prohlížeč událostí přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="77e57-161">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="77e57-162">Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol** pro povolení **analytického** protokolu.</span><span class="sxs-lookup"><span data-stu-id="77e57-162">Right-click **Analytic** and select **Enable Log** to enable the **Analytic** log.</span></span>

9. <span data-ttu-id="77e57-163">Otestujte službu pomocí testovacího klienta WCF dvojitým kliknutím `GetData`.</span><span class="sxs-lookup"><span data-stu-id="77e57-163">Test the service using the WCF test client by double-clicking `GetData`.</span></span>

     <span data-ttu-id="77e57-164">Tím se otevře `GetData` metoda.</span><span class="sxs-lookup"><span data-stu-id="77e57-164">This opens the `GetData` method.</span></span> <span data-ttu-id="77e57-165">Požadavek akceptuje jeden parametr a zajistí, že hodnota je 0, což je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="77e57-165">The request accepts one parameter and ensures that the value is 0, which is the default.</span></span>

     <span data-ttu-id="77e57-166">Klikněte na **vyvolat**.</span><span class="sxs-lookup"><span data-stu-id="77e57-166">Click **Invoke**.</span></span>

10. <span data-ttu-id="77e57-167">Sledujte události vydávané z pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-167">Observe the events emitted from the workflow.</span></span>

     <span data-ttu-id="77e57-168">Přepněte zpět na Prohlížeč událostí a přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="77e57-168">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="77e57-169">Klikněte pravým tlačítkem na možnost **analytické** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="77e57-169">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="77e57-170">Události pracovního postupu se zobrazí v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="77e57-170">The workflow events are displayed in the event viewer.</span></span> <span data-ttu-id="77e57-171">Všimněte si, že se zobrazují události spuštění pracovního postupu a že jeden z nich je Neošetřená výjimka, která odpovídá chybě v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-171">Notice that workflow execution events are displayed and that one of them is an unhandled exception that corresponds to the error in workflow.</span></span> <span data-ttu-id="77e57-172">Kromě toho je vyvolána událost upozornění z aktivity pracovního postupu, která indikuje, že aktivita vyvolává chybu.</span><span class="sxs-lookup"><span data-stu-id="77e57-172">Also, a warning event is emitted from the workflow activity, which indicates that the activity is throwing a fault.</span></span>

11. <span data-ttu-id="77e57-173">Opakujte kroky 9 a 10 se vstupem dat s výjimkou 0, aby nedošlo k žádné chybě.</span><span class="sxs-lookup"><span data-stu-id="77e57-173">Repeat steps 9 and 10 with an input of data other than 0, so that no error is thrown.</span></span>

 <span data-ttu-id="77e57-174">Sledování profilů vám umožní přihlásit se k odběru událostí vygenerovaných modulem runtime při změně stavu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-174">Tracking profiles allow you to subscribe to events that are emitted by the runtime when the state of a workflow instance changes.</span></span> <span data-ttu-id="77e57-175">V závislosti na požadavcích na monitorování můžete vytvořit profil, který je velmi hrubý, který se přihlásí k odběru malé sady změn stavu vysoké úrovně v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="77e57-175">Depending on your monitoring requirements, you can create a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="77e57-176">Na druhé straně můžete vytvořit velmi přesný profil, jehož výstup bude dostatečně bohatý, aby bylo možné provést pozdější opětovné vytvoření provádění.</span><span class="sxs-lookup"><span data-stu-id="77e57-176">On the other hand, you can create a very precise profile whose output is rich enough to reconstruct the execution later.</span></span> <span data-ttu-id="77e57-177">Ukázka demonstruje události emitované z modulu runtime pracovního postupu do ETW pomocí nástroje `HealthMonitoring Tracking Profile`, který generuje malou sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="77e57-177">The sample demonstrates the events emitted from the workflow runtime to ETW using the `HealthMonitoring Tracking Profile`, which emits a small set of events.</span></span> <span data-ttu-id="77e57-178">Jiný profil, který generuje další události sledování pracovního postupu, je k dispozici také v souboru Web. config `Troubleshooting Tracking Profile`, který je pojmenován.</span><span class="sxs-lookup"><span data-stu-id="77e57-178">A different profile that emits more workflow tracking events is also provided in the Web.config that is named `Troubleshooting Tracking Profile`.</span></span> <span data-ttu-id="77e57-179">Při instalaci nástroje je v souboru Machine. config nakonfigurován výchozí profil s prázdným názvem. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77e57-179">When the [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] is installed, a default profile with an empty name is configured in the Machine.config file.</span></span> <span data-ttu-id="77e57-180">Tento profil se používá v konfiguraci chování sledování trasování událostí pro Windows, pokud není zadaný název profilu ani název prázdného profilu.</span><span class="sxs-lookup"><span data-stu-id="77e57-180">This profile is used by the ETW tracking behavior configuration when no profile name or an empty profile name is specified.</span></span>

 <span data-ttu-id="77e57-181">Profil sledování stavu vygeneruje záznamy instancí pracovního postupu a záznamy šíření chyb aktivity.</span><span class="sxs-lookup"><span data-stu-id="77e57-181">The health monitoring tracking profile emits workflow instance records and activity fault propagation records.</span></span> <span data-ttu-id="77e57-182">Tento profil je vytvořen přidáním následujícího profilu sledování do konfiguračního souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="77e57-182">This profile is created by adding the following tracking profile to a Web.config configuration file.</span></span>

```xml
<<tracking>
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

 <span data-ttu-id="77e57-183">Profil se dá změnit tak, že změníte `EtwTrackingParticipant` konfiguraci na následující.</span><span class="sxs-lookup"><span data-stu-id="77e57-183">The profile can be changed by changing the `EtwTrackingParticipant` configuration to the following.</span></span>

```xml
<behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="HealthMonitoring Tracking Profile"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
```

#### <a name="to-clean-up-optional"></a><span data-ttu-id="77e57-184">Vyčištění (volitelné)</span><span class="sxs-lookup"><span data-stu-id="77e57-184">To clean up (Optional)</span></span>

1. <span data-ttu-id="77e57-185">Otevřete Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="77e57-185">Open Event Viewer.</span></span>

2. <span data-ttu-id="77e57-186">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="77e57-186">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="77e57-187">Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **zakázat protokol**.</span><span class="sxs-lookup"><span data-stu-id="77e57-187">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="77e57-188">Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="77e57-188">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="77e57-189">Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **Vymazat protokol**.</span><span class="sxs-lookup"><span data-stu-id="77e57-189">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="77e57-190">Kliknutím na možnost **Vymazat** vymažte události.</span><span class="sxs-lookup"><span data-stu-id="77e57-190">Choose the **Clear** option to clear the events.</span></span>

## <a name="known-issue"></a><span data-ttu-id="77e57-191">Známý problém</span><span class="sxs-lookup"><span data-stu-id="77e57-191">Known Issue</span></span>

> [!NOTE]
> <span data-ttu-id="77e57-192">Došlo k známému problému Prohlížeč událostí, kde se nemusí podařit dekódovat události ETW.</span><span class="sxs-lookup"><span data-stu-id="77e57-192">There is a known issue in the Event Viewer where it may fail to decode ETW events.</span></span> <span data-ttu-id="77e57-193">Může se zobrazit chybová zpráva, která vypadá nějak takto:</span><span class="sxs-lookup"><span data-stu-id="77e57-193">You may see an error message that looks like the following.</span></span>
>
>  <span data-ttu-id="77e57-194">Popis události \<ID ID > ze zdrojového serveru Microsoft-Windows-Application Server – aplikace se nenašly.</span><span class="sxs-lookup"><span data-stu-id="77e57-194">The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="77e57-195">Buď není v místním počítači nainstalována komponenta, která vyvolává tuto událost, nebo je instalace poškozena.</span><span class="sxs-lookup"><span data-stu-id="77e57-195">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="77e57-196">Součást můžete nainstalovat nebo opravit v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="77e57-196">You can install or repair the component on the local computer.</span></span>
>
>  <span data-ttu-id="77e57-197">Pokud k této chybě dojde, klikněte v podokně akce na aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="77e57-197">If you encounter this error, click refresh in the actions pane.</span></span> <span data-ttu-id="77e57-198">Událost by se teď měla dekódovat správně.</span><span class="sxs-lookup"><span data-stu-id="77e57-198">The event should now decode properly.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="77e57-199">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="77e57-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="77e57-200">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="77e57-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="77e57-201">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="77e57-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="77e57-202">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="77e57-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\EtwTracking`  
  
## <a name="see-also"></a><span data-ttu-id="77e57-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77e57-203">See also</span></span>

- [<span data-ttu-id="77e57-204">Ukázky monitorování technologie AppFabric</span><span class="sxs-lookup"><span data-stu-id="77e57-204">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
