---
title: Konfigurace sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: c9d38533d11497bd4404e4f8795d8a1ce9b17df9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491253"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="29696-102">Konfigurace sledování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="29696-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="29696-103">Pracovní postup můžete provést třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="29696-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="29696-104">Hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="29696-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="29696-105">Provést, protože <xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="29696-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="29696-106">Proveden přímo pomocí <xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="29696-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="29696-107">V závislosti na pracovním postupu možnost hostování sledování účastník přidat buď prostřednictvím kódu nebo konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="29696-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="29696-108">Toto téma popisuje, jak je sledování nakonfigurované tak, že přidáte sledování účastník <xref:System.Activities.WorkflowApplication> a získat <xref:System.ServiceModel.Activities.WorkflowServiceHost>a jak povolit sledování při použití <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="29696-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="29696-109">Konfigurace sledování aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="29696-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="29696-110">Pracovní postup můžete spustit pomocí <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="29696-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="29696-111">Toto téma popisuje konfiguraci sledování pro [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] aplikace pracovního postupu tak, že přidáte sledování účastník <xref:System.Activities.WorkflowApplication> hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="29696-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="29696-112">V takovém případě pracovní postup spouští jako aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="29696-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="29696-113">Nakonfigurovat aplikace pracovního postupu pomocí kódu (spíše než pomocí konfiguračního souboru), který je v místním prostředí .exe souboru pomocí <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="29696-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="29696-114">Sledování účastník bude přidán jako rozšíření <xref:System.Activities.WorkflowApplication> instance.</span><span class="sxs-lookup"><span data-stu-id="29696-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="29696-115">To se provádí tak, že přidáte <xref:System.Activities.Tracking.TrackingParticipant> do kolekce rozšíření pro instanci aplikace WorkflowApplication.</span><span class="sxs-lookup"><span data-stu-id="29696-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="29696-116">Pro aplikace pracovního postupu můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> rozšíření chování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="29696-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

```csharp
LogActivity activity = new LogActivity();

WorkflowApplication instance = new WorkflowApplication(activity);
EtwTrackingParticipant trackingParticipant =
    new EtwTrackingParticipant
{

        TrackingProfile = new TrackingProfile
           {
               Name = "SampleTrackingProfile",
               ActivityDefinitionId = "ProcessOrder",
               Queries = new WorkflowInstanceQuery
               {
                  States = { "*" }
              }
          }
       };
instance.Extensions.Add(trackingParticipant);
```

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="29696-117">Konfigurace sledování služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="29696-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="29696-118">Pracovní postup může být vystavena jako služba WCF při hostování v <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="29696-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="29696-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> je specializovaná implementace .NET ServiceHost pro nějakou službu založenou na pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="29696-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="29696-120">Tato část vysvětluje postup konfigurace sledování [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] používané služby pracovního postupu <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="29696-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="29696-121">Je nakonfigurovaný pomocí souboru Web.config (pro Web hostované služby) nebo soubor App.config (pro služby hostované v samostatné aplikaci, jako je například aplikace konzoly) zadáním chování služby nebo pomocí kódu přidáním specifické pro sledování chování <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce pro tohoto hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="29696-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="29696-122">Pro pracovní postup služby hostované v <xref:System.ServiceModel.WorkflowServiceHost>, můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> element v konfiguračním souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="29696-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
<behaviors>
```

<span data-ttu-id="29696-123">Můžete také služby pracovního postupu hostované v <xref:System.ServiceModel.WorkflowServiceHost>, můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> rozšíření chování prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="29696-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="29696-124">Chcete-li přidat vlastní sledování účastník, vytvořit nové rozšíření chování a přidejte ho do <xref:System.ServiceModel.ServiceHost> jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="29696-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="29696-125">Pokud chcete zobrazit ukázkový kód, který ukazuje, jak vytvořit vlastní chování element, který přidá vlastní sledování účastník, přečtěte si [sledování](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="29696-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>

```csharp
ServiceHost svcHost = new ServiceHost(typeof(WorkflowService), new
                                 Uri("http://localhost:8001/Sample"));
EtwTrackingBehavior trackingBehavior =
    new EtwTrackingBehavior
    {
        ProfileName = "Sample Tracking Profile"
    };
svcHost.Description.Behaviors.Add(trackingBehavior);
svcHost.Open();
```

<span data-ttu-id="29696-126">Účastník sledování se přidá k hostiteli služby pracovního postupu jako rozšíření chování.</span><span class="sxs-lookup"><span data-stu-id="29696-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="29696-127">Následující ukázkový kód ukazuje, jak číst z konfiguračního souboru profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="29696-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            if (profileName == null)
            {
                profileName = "";
            }

            //Find the profile with the specified profile name in the list of profile found in config
            var match = from p in new List<TrackingProfile>(trackingSection.TrackingProfiles)
                        where (p.Name == profileName) && ((p.ActivityDefinitionId == displayName) || (p.ActivityDefinitionId == "*"))
                        select p;

            if (match.Count() == 0)
            {
                //return an empty profile
                trackingProfile = new TrackingProfile()
                {
                    ActivityDefinitionId = displayName
                };

            }
            else
            {
                trackingProfile = match.First();
            }

            return trackingProfile;
```

<span data-ttu-id="29696-128">Tento ukázkový kód ukazuje, jak přidat profil sledování do hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="29696-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

```csharp
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;
if (null != workflowServiceHost)
{
    string workflowDisplayName = workflowServiceHost.Activity.DisplayName;
    TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);
    workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant {
        TrackingProfile = trackingProfile
    });
 }
```

> [!NOTE]
> <span data-ttu-id="29696-129">Další informace o sledování profilů najdete [sledování profilů](https://go.microsoft.com/fwlink/?LinkId=201310).</span><span class="sxs-lookup"><span data-stu-id="29696-129">For more information on tracking profiles, refer to [Tracking Profiles](https://go.microsoft.com/fwlink/?LinkId=201310).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="29696-130">Konfigurace sledování pomocí WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="29696-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="29696-131">Konfigurace sledování pracovního postupu spuštěn pomocí <xref:System.Activities.WorkflowInvoker>, přidejte zprostředkovatele sledování jako rozšíření <xref:System.Activities.WorkflowInvoker> instance.</span><span class="sxs-lookup"><span data-stu-id="29696-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="29696-132">Následující příklad kódu je z [vlastní sledování](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="29696-132">The following code example is from the [Custom Tracking](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="29696-133">Zobrazení sledování záznamů v prohlížeči událostí</span><span class="sxs-lookup"><span data-stu-id="29696-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="29696-134">Existují dva protokoly Prohlížeče událostí zajímají hlavně o zobrazení při sledování provádění pracovního postupu - analýzy protokolů a protokolů ladění.</span><span class="sxs-lookup"><span data-stu-id="29696-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="29696-135">Obě nacházet v rámci Microsoft&#124;Windows&#124;uzlu serveru aplikace.</span><span class="sxs-lookup"><span data-stu-id="29696-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="29696-136">Protokoly v této části obsahují události z jedné aplikace, nikoli události, které mají vliv na celý systém.</span><span class="sxs-lookup"><span data-stu-id="29696-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="29696-137">Ladění trasování, které události se zapisují do protokolů ladění.</span><span class="sxs-lookup"><span data-stu-id="29696-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="29696-138">Shromažďování událostí trasování ladění pracovního postupu v prohlížeči událostí, povolte protokol ladění.</span><span class="sxs-lookup"><span data-stu-id="29696-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="29696-139">Chcete-li spustit nástroj Prohlížeč událostí, klikněte na tlačítko **Start**a potom klikněte na tlačítko **spustit.**</span><span class="sxs-lookup"><span data-stu-id="29696-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="29696-140">V dialogu Spustit zadejte `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="29696-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="29696-141">V dialogovém okně prohlížeče událostí, rozbalte **protokoly aplikací a služeb** uzlu.</span><span class="sxs-lookup"><span data-stu-id="29696-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="29696-142">Rozbalte **Microsoft**, **Windows**, a **aplikace Server-** uzly.</span><span class="sxs-lookup"><span data-stu-id="29696-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="29696-143">Klikněte pravým tlačítkem myši **ladění** pod uzlem **Server aplikace** uzel a vyberte možnost **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="29696-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="29696-144">Spusťte vaši aplikaci povoleno trasování generovat události trasování.</span><span class="sxs-lookup"><span data-stu-id="29696-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="29696-145">Klikněte pravým tlačítkem myši **ladění** uzel a vyberte možnost **aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="29696-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="29696-146">Trasování událostí by se zobrazovat v prostředním podokně.</span><span class="sxs-lookup"><span data-stu-id="29696-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="29696-147">WF 4 poskytuje sledování účastník, který zapíše záznamy sledování k relaci ETW (událost trasování pro Windows).</span><span class="sxs-lookup"><span data-stu-id="29696-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="29696-148">Účastník sledování ETW konfigurován pomocí sledování profil přihlásit k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="29696-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="29696-149">Pokud je povoleno sledování, chyby sledování záznamů je vygenerován pro trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="29696-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="29696-150">Trasování událostí pro Windows Sledování událostí (v rozsahu 100 113) od odpovídající, protože ho vygeneroval účastník sledování ETW sledování události se zapisují do v analytickém protokolu.</span><span class="sxs-lookup"><span data-stu-id="29696-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="29696-151">Chcete-li zobrazit záznamy sledování, postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="29696-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="29696-152">Chcete-li spustit nástroj Prohlížeč událostí, klikněte na tlačítko **Start**a potom klikněte na tlačítko **spustit.**</span><span class="sxs-lookup"><span data-stu-id="29696-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="29696-153">V dialogu Spustit zadejte `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="29696-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="29696-154">V dialogovém okně prohlížeče událostí, rozbalte **protokoly aplikací a služeb** uzlu.</span><span class="sxs-lookup"><span data-stu-id="29696-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="29696-155">Rozbalte **Microsoft**, **Windows**, a **aplikace Server-** uzly.</span><span class="sxs-lookup"><span data-stu-id="29696-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="29696-156">Klikněte pravým tlačítkem myši **analytické** pod uzlem **Server aplikace** uzel a vyberte možnost **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="29696-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="29696-157">Spuštění vaší aplikace s povolenými sledování k vygenerování záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="29696-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="29696-158">Klikněte pravým tlačítkem myši **analytické** uzel a vyberte možnost **aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="29696-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="29696-159">Sledování záznamů by se zobrazovat v prostředním podokně.</span><span class="sxs-lookup"><span data-stu-id="29696-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="29696-160">Sledování událostí v prohlížeči událostí na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="29696-160">The following image shows tracking events in the event viewer.</span></span>

<span data-ttu-id="29696-161">![Zobrazení prohlížeče událostí sledování záznamů](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")</span><span class="sxs-lookup"><span data-stu-id="29696-161">![Event Viewer showing tracking records](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")</span></span>

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="29696-162">Registrace poskytovatele specifické pro aplikaci ID</span><span class="sxs-lookup"><span data-stu-id="29696-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="29696-163">Pokud události se zapisují do protokolu konkrétní aplikaci, použijte následující postup zaregistrovat nový manifest zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="29696-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="29696-164">Deklarujte ID zprostředkovatele v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="29696-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="29696-165">Zkopírujte soubor manifestu z %windir%\Microsoft.NET\Framework\\< nejnovější verzi [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man do dočasného umístění a přejmenujte ho na Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span><span class="sxs-lookup"><span data-stu-id="29696-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="29696-166">Změňte na nové GUID identifikátoru GUID v souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="29696-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. <span data-ttu-id="29696-167">Pokud nechcete odinstalovat výchozího zprostředkovatele, změňte název zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="29696-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. <span data-ttu-id="29696-168">Pokud jste změnili název zprostředkovatele v předchozím kroku, změňte názvy kanálů v souboru manifestu na nový název poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="29696-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="29696-169">Vygenerujte prostředek knihovny DLL pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="29696-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="29696-170">Nainstalujte Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="29696-170">Install the Windows SDK.</span></span> <span data-ttu-id="29696-171">Sada Windows SDK obsahuje kompilátor zprávy ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) a kompilátor prostředků ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).</span><span class="sxs-lookup"><span data-stu-id="29696-171">The Windows SDK includes the message compiler ([mc.exe](https://go.microsoft.com/fwlink/?LinkId=184606)) and resource compiler ([rc.exe](https://go.microsoft.com/fwlink/?LinkId=184605)).</span></span>

    2. <span data-ttu-id="29696-172">V příkazovém řádku Windows SDK spusťte mc.exe na nový soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="29696-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="29696-173">Spusťte rc.exe na soubor prostředků vygenerované v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="29696-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="29696-174">Vytvořte soubor prázdný cs názvem NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="29696-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="29696-175">Vytvořte prostředek knihovny DLL pomocí kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="29696-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="29696-176">Změnit název knihovny dll prostředků a zprávy v souboru manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nový název knihovny dll.</span><span class="sxs-lookup"><span data-stu-id="29696-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. <span data-ttu-id="29696-177">Použití [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) k registraci manifestu.</span><span class="sxs-lookup"><span data-stu-id="29696-177">Use [wevtutil](https://go.microsoft.com/fwlink/?LinkId=184608) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="29696-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29696-178">See also</span></span>

- [<span data-ttu-id="29696-179">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="29696-179">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="29696-180">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="29696-180">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
