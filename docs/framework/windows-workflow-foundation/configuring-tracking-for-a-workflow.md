---
title: Konfigurace sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 97b25873e9f20d5d390b7a59531b3a5af32296df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802671"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="b27ff-102">Konfigurace sledování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b27ff-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="b27ff-103">Pracovní postup může být proveden třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="b27ff-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="b27ff-104">Hostovaná v <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="b27ff-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="b27ff-105">Spuštěno jako <xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="b27ff-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="b27ff-106">Provedeno přímo pomocí <xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="b27ff-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="b27ff-107">V závislosti na možnosti hostování pracovního postupu lze sledování účastníka přidat prostřednictvím kódu nebo prostřednictvím konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b27ff-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="b27ff-108">Toto téma popisuje, jak je sledování nakonfigurováno přidáním účastníka sledování do <xref:System.Activities.WorkflowApplication> a do <xref:System.ServiceModel.Activities.WorkflowServiceHost>a jak povolit sledování při použití <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="b27ff-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="b27ff-109">Konfigurace sledování aplikace pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b27ff-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="b27ff-110">Pracovní postup lze spustit pomocí <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="b27ff-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="b27ff-111">V tomto tématu se dozvíte, jak je sledování nakonfigurované pro [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] aplikace pracovního postupu, a to přidáním účastníka sledování do hostitele pracovního postupu <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="b27ff-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="b27ff-112">V takovém případě pracovní postup běží jako aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b27ff-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="b27ff-113">Můžete nakonfigurovat aplikaci pracovního postupu prostřednictvím kódu (nikoli pomocí konfiguračního souboru), což je samostatný soubor. exe s použitím třídy <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="b27ff-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="b27ff-114">Účastník sledování je přidán jako rozšíření instance <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="b27ff-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="b27ff-115">To se provádí přidáním <xref:System.Activities.Tracking.TrackingParticipant> do kolekce rozšíření pro instanci WorkflowApplication.</span><span class="sxs-lookup"><span data-stu-id="b27ff-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="b27ff-116">U aplikace pracovního postupu můžete přidat rozšíření chování <xref:System.Activities.Tracking.EtwTrackingParticipant>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b27ff-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

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

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="b27ff-117">Konfigurace sledování služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="b27ff-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="b27ff-118">Pracovní postup může být vystavený jako služba WCF při hostování v hostiteli služby <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b27ff-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="b27ff-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> je specializovaná implementace rozhraní ServiceHost .NET pro službu založenou na pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="b27ff-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="b27ff-120">V této části se dozvíte, jak nakonfigurovat sledování pro službu [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Workflow Service spuštěnou v <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="b27ff-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="b27ff-121">Je nakonfigurována pomocí souboru Web. config (pro službu hostovanou na webu) nebo souboru App. config (pro službu hostovanou v samostatné aplikaci, jako je například Konzolová aplikace), zadáním chování služby nebo prostřednictvím kódu přidáním určitého chování pro sledování do kolekce <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="b27ff-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="b27ff-122">Pro službu pracovního postupu, která je hostována v <xref:System.ServiceModel.WorkflowServiceHost>, můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> elementu v konfiguračním souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b27ff-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="b27ff-123">Alternativně můžete pro službu pracovního postupu hostované v <xref:System.ServiceModel.WorkflowServiceHost>přidat rozšíření chování <xref:System.Activities.Tracking.EtwTrackingParticipant> prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="b27ff-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="b27ff-124">Chcete-li přidat vlastního účastníka sledování, vytvořte nové rozšíření chování a přidejte ho do <xref:System.ServiceModel.ServiceHost>, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="b27ff-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="b27ff-125">Chcete-li zobrazit vzorový kód, který ukazuje, jak vytvořit vlastní prvek chování, který přidá vlastního účastníka sledování, přečtěte si ukázky [sledování](./samples/tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="b27ff-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

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

<span data-ttu-id="b27ff-126">Účastník sledování se přidá do hostitele služby pracovního postupu jako rozšíření chování.</span><span class="sxs-lookup"><span data-stu-id="b27ff-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="b27ff-127">Následující vzorový kód ukazuje, jak číst profil sledování z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b27ff-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

```csharp
TrackingProfile GetProfile(string profileName, string displayName)
        {
            TrackingProfile trackingProfile = null;
            TrackingSection trackingSection = (TrackingSection)WebConfigurationManager.GetSection("system.serviceModel/tracking");
            if (trackingSection == null)
            {
                return null;
            }

            profileName ??= "";

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

<span data-ttu-id="b27ff-128">Tento vzorový kód ukazuje, jak přidat profil sledování do hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b27ff-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

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
> <span data-ttu-id="b27ff-129">Další informace o sledování profilů najdete v tématu [sledování profilů](tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b27ff-129">For more information on tracking profiles, refer to [Tracking Profiles](tracking-profiles.md).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="b27ff-130">Konfigurace sledování pomocí WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="b27ff-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="b27ff-131">Ke konfiguraci sledování pracovního postupu spuštěného pomocí <xref:System.Activities.WorkflowInvoker>přidejte zprostředkovatele sledování jako rozšíření do instance <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="b27ff-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="b27ff-132">Následující příklad kódu je z vlastní ukázky [sledování](./samples/custom-tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="b27ff-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="b27ff-133">Zobrazení záznamů sledování v Prohlížeč událostí</span><span class="sxs-lookup"><span data-stu-id="b27ff-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="b27ff-134">Existují dva Prohlížeč událostí protokoly, které se týkají zvláštního zájmu k zobrazení při sledování provádění technologie WF – analytického protokolu a protokolu ladění.</span><span class="sxs-lookup"><span data-stu-id="b27ff-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="b27ff-135">Oba se nacházejí v uzlu aplikace&#124;serveru&#124;Microsoft Windows – aplikace.</span><span class="sxs-lookup"><span data-stu-id="b27ff-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="b27ff-136">Protokoly v této části obsahují události z jedné aplikace a nikoli události, které mají vliv na celý systém.</span><span class="sxs-lookup"><span data-stu-id="b27ff-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="b27ff-137">Události trasování ladění se zapisují do protokolu ladění.</span><span class="sxs-lookup"><span data-stu-id="b27ff-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="b27ff-138">Chcete-li shromáždit události trasování ladění WF v Prohlížeč událostí, povolte protokol ladění.</span><span class="sxs-lookup"><span data-stu-id="b27ff-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="b27ff-139">Chcete-li otevřít Prohlížeč událostí, klikněte na tlačítko **Start**a poté klikněte na příkaz **Spustit.**</span><span class="sxs-lookup"><span data-stu-id="b27ff-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="b27ff-140">V dialogovém okně Spustit zadejte `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="b27ff-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="b27ff-141">V dialogovém okně Prohlížeč událostí rozbalte uzel **protokoly aplikací a služeb** .</span><span class="sxs-lookup"><span data-stu-id="b27ff-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="b27ff-142">Rozbalte uzly **Microsoft**, **Windows**a **aplikační server – aplikace** .</span><span class="sxs-lookup"><span data-stu-id="b27ff-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="b27ff-143">Klikněte pravým tlačítkem myši na uzel **ladění** v uzlu **aplikační server – aplikace** a vyberte **Povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="b27ff-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="b27ff-144">Spusťte aplikaci s povoleným trasováním a vygenerujte události trasování.</span><span class="sxs-lookup"><span data-stu-id="b27ff-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="b27ff-145">Klikněte pravým tlačítkem na uzel **ladění** a vyberte **aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="b27ff-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="b27ff-146">Události trasování by měly být viditelné v prostředním podokně.</span><span class="sxs-lookup"><span data-stu-id="b27ff-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="b27ff-147">WF 4 poskytuje účastníkovi sledování, který zapisuje záznamy sledování do relace ETW (trasování událostí pro Windows).</span><span class="sxs-lookup"><span data-stu-id="b27ff-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="b27ff-148">Účastník sledování ETW je nakonfigurovaný s profilem sledování, aby se mohl přihlásit k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="b27ff-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="b27ff-149">Pokud je povoleno sledování, jsou záznamy sledování chyb generovány do ETW.</span><span class="sxs-lookup"><span data-stu-id="b27ff-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="b27ff-150">Události sledování ETW (mezi rozsahem 100-113) odpovídající sledovacím událostem vygenerovaným účastníkem sledování ETW jsou zapisovány do analytického protokolu.</span><span class="sxs-lookup"><span data-stu-id="b27ff-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="b27ff-151">Chcete-li zobrazit záznamy sledování, postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="b27ff-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="b27ff-152">Chcete-li otevřít Prohlížeč událostí, klikněte na tlačítko **Start**a poté klikněte na příkaz **Spustit.**</span><span class="sxs-lookup"><span data-stu-id="b27ff-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="b27ff-153">V dialogovém okně Spustit zadejte `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="b27ff-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="b27ff-154">V dialogovém okně Prohlížeč událostí rozbalte uzel **protokoly aplikací a služeb** .</span><span class="sxs-lookup"><span data-stu-id="b27ff-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="b27ff-155">Rozbalte uzly **Microsoft**, **Windows**a **aplikační server – aplikace** .</span><span class="sxs-lookup"><span data-stu-id="b27ff-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="b27ff-156">Klikněte pravým tlačítkem myši **na uzel Analytics v uzlu** **aplikační server – aplikace** a vyberte možnost **Povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="b27ff-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="b27ff-157">Spusťte aplikaci s povoleným sledováním pro generování záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="b27ff-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="b27ff-158">Klikněte pravým tlačítkem **na uzel analýzy** a vyberte **aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="b27ff-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="b27ff-159">Záznamy sledování by se měly zobrazit v prostředním podokně.</span><span class="sxs-lookup"><span data-stu-id="b27ff-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="b27ff-160">Následující obrázek ukazuje sledování událostí v prohlížeči událostí:</span><span class="sxs-lookup"><span data-stu-id="b27ff-160">The following image shows tracking events in the event viewer:</span></span>

![Snímek obrazovky Prohlížeč událostí zobrazující záznamy o sledování](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="b27ff-162">Registrace ID zprostředkovatele specifického pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="b27ff-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="b27ff-163">Pokud je třeba události zapsat do konkrétního protokolu aplikace, použijte následující postup k registraci nového manifestu poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="b27ff-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="b27ff-164">Deklarujete ID zprostředkovatele v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b27ff-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="b27ff-165">Zkopírujte soubor manifestu z%windir%\Microsoft.NET\Framework\\\<nejnovější verzi [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man na dočasné umístění a přejmenujte ho na Microsoft. Windows. ApplicationServer. Applications_Provider1. Man.</span><span class="sxs-lookup"><span data-stu-id="b27ff-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="b27ff-166">Změňte identifikátor GUID v souboru manifestu na nový identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="b27ff-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

4. <span data-ttu-id="b27ff-167">Pokud nechcete odinstalovat výchozího zprostředkovatele, změňte název zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="b27ff-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"
    ```

5. <span data-ttu-id="b27ff-168">Pokud jste v předchozím kroku změnili název poskytovatele, změňte názvy kanálů v souboru manifestu na název nového poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="b27ff-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="b27ff-169">Vygenerujte DLL prostředku pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="b27ff-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="b27ff-170">Nainstalujte Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="b27ff-170">Install the Windows SDK.</span></span> <span data-ttu-id="b27ff-171">Windows SDK obsahuje kompilátor zpráv ([MC. exe](/windows/win32/wes/message-compiler--mc-exe-)) a kompilátor prostředků ([RC. exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span><span class="sxs-lookup"><span data-stu-id="b27ff-171">The Windows SDK includes the message compiler ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) and resource compiler ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span></span>

    2. <span data-ttu-id="b27ff-172">Na příkazovém řádku Windows SDK spusťte příkaz MC. exe na novém souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="b27ff-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="b27ff-173">Spusťte RC. exe v souboru prostředků vygenerovaném v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="b27ff-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="b27ff-174">Vytvořte prázdný soubor cs s názvem NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="b27ff-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="b27ff-175">Vytvořte DLL prostředku pomocí C# kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="b27ff-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="b27ff-176">Změňte název knihovny DLL prostředku a zprávy v souboru manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nový název knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="b27ff-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">
        ```

    7. <span data-ttu-id="b27ff-177">K registraci manifestu použijte [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) .</span><span class="sxs-lookup"><span data-stu-id="b27ff-177">Use [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="b27ff-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b27ff-178">See also</span></span>

- <span data-ttu-id="b27ff-179">[Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b27ff-179">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="b27ff-180">[Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b27ff-180">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
