---
title: Konfigurace sledování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
ms.openlocfilehash: 5ec94d6b8e58012d0c5c8ca8593c3cef81cd9ec3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248209"
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="1fc06-102">Konfigurace sledování pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1fc06-102">Configuring Tracking for a Workflow</span></span>

<span data-ttu-id="1fc06-103">Pracovní postup lze spustit třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="1fc06-103">A workflow can execute in three ways:</span></span>

- <span data-ttu-id="1fc06-104">Hostované v<xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="1fc06-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>

- <span data-ttu-id="1fc06-105">Popraven jako<xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="1fc06-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>

- <span data-ttu-id="1fc06-106">Spuštěno přímo pomocí<xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="1fc06-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>

<span data-ttu-id="1fc06-107">V závislosti na možnosti hostování pracovního postupu lze účastníka sledování přidat buď prostřednictvím kódu, nebo prostřednictvím konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="1fc06-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="1fc06-108">Toto téma popisuje, jak je sledování konfigurováno přidáním účastníka <xref:System.Activities.WorkflowApplication> sledování do a <xref:System.ServiceModel.Activities.WorkflowServiceHost>a , a jak povolit sledování při použití <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="1fc06-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>

## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="1fc06-109">Konfigurace sledování aplikací pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1fc06-109">Configuring Workflow Application Tracking</span></span>

<span data-ttu-id="1fc06-110">Pracovní postup lze <xref:System.Activities.WorkflowApplication> spustit pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="1fc06-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="1fc06-111">Toto téma ukazuje, jak [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] je sledování konfigurováno pro <xref:System.Activities.WorkflowApplication> aplikaci pracovního postupu přidáním účastníka sledování do hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="1fc06-112">V tomto případě je pracovní postup spuštěn jako aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="1fc06-113">Aplikaci pracovního postupu nakonfigurujete prostřednictvím kódu (nikoli pomocí konfiguračního souboru), což je samoobslužný soubor .exe používající třídu. <xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="1fc06-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="1fc06-114">Účastník sledování je přidán jako <xref:System.Activities.WorkflowApplication> rozšíření instance.</span><span class="sxs-lookup"><span data-stu-id="1fc06-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="1fc06-115">To se provádí <xref:System.Activities.Tracking.TrackingParticipant> přidáním kolekce rozšíření pro instanci WorkflowApplication.</span><span class="sxs-lookup"><span data-stu-id="1fc06-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>

<span data-ttu-id="1fc06-116">Pro aplikaci pracovního postupu <xref:System.Activities.Tracking.EtwTrackingParticipant> můžete přidat rozšíření chování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>

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

### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="1fc06-117">Konfigurace sledování služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1fc06-117">Configuring Workflow Service Tracking</span></span>

<span data-ttu-id="1fc06-118">Pracovní postup může být vystaven jako služba WCF při hostování v hostiteli služby. <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="1fc06-118">A workflow can be exposed as a WCF service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="1fc06-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost>je specializovaná implementace služby .NET ServiceHost pro službu založenou na pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="1fc06-120">Tato část vysvětluje, jak nakonfigurovat sledování pro službu pracovního postupu spuštěnou [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v aplikaci <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1fc06-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="1fc06-121">Je konfigurován prostřednictvím souboru Web.config (pro webovou hostovanou službu) nebo souboru App.config (pro službu hostovanou v samostatné aplikaci, například v aplikaci konzoly) zadáním chování služby nebo prostřednictvím kódu přidáním chování specifického pro sledování do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="1fc06-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>

<span data-ttu-id="1fc06-122">Pro službu pracovního <xref:System.ServiceModel.WorkflowServiceHost>postupu hostovoje v aplikaci můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> prvek v konfiguračním souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>

```xml
<behaviors>
   <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
   </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="1fc06-123">Případně pro službu pracovního <xref:System.ServiceModel.WorkflowServiceHost>postupu hostované <xref:System.Activities.Tracking.EtwTrackingParticipant> v aplikaci můžete přidat rozšíření chování prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="1fc06-124">Chcete-li přidat vlastní účastníksledování, vytvořte nové <xref:System.ServiceModel.ServiceHost> rozšíření chování a přidejte jej tak, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>

> [!NOTE]
> <span data-ttu-id="1fc06-125">Pokud chcete zobrazit ukázkový kód, který ukazuje, jak vytvořit vlastní prvek chování, který přidá vlastní účastníka sledování, podívejte se na [sledování](./samples/tracking.md) vzorků.</span><span class="sxs-lookup"><span data-stu-id="1fc06-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](./samples/tracking.md) samples.</span></span>

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

<span data-ttu-id="1fc06-126">Účastník sledování je přidán do hostitele služby pracovního postupu jako rozšíření chování.</span><span class="sxs-lookup"><span data-stu-id="1fc06-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>

<span data-ttu-id="1fc06-127">Tento ukázkový kód níže ukazuje, jak číst profil sledování z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="1fc06-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>

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

<span data-ttu-id="1fc06-128">Tento ukázkový kód ukazuje, jak přidat profil sledování do hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>

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
> <span data-ttu-id="1fc06-129">Další informace o profilech sledování naleznete [v informacích o profilech sledování](tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1fc06-129">For more information on tracking profiles, refer to [Tracking Profiles](tracking-profiles.md).</span></span>

### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="1fc06-130">Konfigurace sledování pomocí workflowinvokeru</span><span class="sxs-lookup"><span data-stu-id="1fc06-130">Configuring tracking using WorkflowInvoker</span></span>

<span data-ttu-id="1fc06-131">Chcete-li nakonfigurovat sledování <xref:System.Activities.WorkflowInvoker>pracovního postupu prováděného pomocí <xref:System.Activities.WorkflowInvoker> , přidejte zprostředkovatele sledování jako rozšíření instance.</span><span class="sxs-lookup"><span data-stu-id="1fc06-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="1fc06-132">Následující příklad kódu je z [ukázky vlastní sledování.](./samples/custom-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="1fc06-132">The following code example is from the [Custom Tracking](./samples/custom-tracking.md) sample.</span></span>

```csharp
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());
invoker.Extensions.Add(customTrackingParticipant);
invoker.Invoke();
```

### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="1fc06-133">Zobrazení záznamů sledování v Prohlížeči událostí</span><span class="sxs-lookup"><span data-stu-id="1fc06-133">Viewing tracking records in Event Viewer</span></span>

<span data-ttu-id="1fc06-134">Existují dva protokoly prohlížeče událostí, které jsou zvláště zajímavé při sledování provádění služby WF - protokol Analytic a protokol ladění.</span><span class="sxs-lookup"><span data-stu-id="1fc06-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="1fc06-135">Obě jsou umístěny pod uzu Microsoft&#124;Windows&#124;Application Server-Applications.</span><span class="sxs-lookup"><span data-stu-id="1fc06-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span> <span data-ttu-id="1fc06-136">Protokoly v této části obsahují události z jedné aplikace, nikoli události, které mají vliv na celý systém.</span><span class="sxs-lookup"><span data-stu-id="1fc06-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>

<span data-ttu-id="1fc06-137">Ladění trasování události jsou zapsány do protokolu ladění.</span><span class="sxs-lookup"><span data-stu-id="1fc06-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="1fc06-138">Chcete-li shromažďovat události trasování ladění wf v Prohlížeči událostí, povolte protokol ladění.</span><span class="sxs-lookup"><span data-stu-id="1fc06-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>

1. <span data-ttu-id="1fc06-139">Pokud chcete spustit Prohlížeč událostí, klikněte na **Tlačítko Start**a potom klikněte na **Spustit.**</span><span class="sxs-lookup"><span data-stu-id="1fc06-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="1fc06-140">V dialogovém okně `eventvwr`Spustit zadejte .</span><span class="sxs-lookup"><span data-stu-id="1fc06-140">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="1fc06-141">V dialogovém okně Prohlížeč událostí rozbalte uzel **Protokoly aplikací a služeb.**</span><span class="sxs-lookup"><span data-stu-id="1fc06-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="1fc06-142">Rozbalte uzly **Microsoft**, **Windows**a **Application Server-Applications.**</span><span class="sxs-lookup"><span data-stu-id="1fc06-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="1fc06-143">Klepněte pravým tlačítkem myši na uzel **Ladění** pod uzlemi **Aplikační server-aplikace** a vyberte **příkaz Povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="1fc06-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="1fc06-144">Spusťte aplikaci s povoleným trasování a vygenerujte události trasování.</span><span class="sxs-lookup"><span data-stu-id="1fc06-144">Execute your tracing-enabled application to generate tracing events.</span></span>

6. <span data-ttu-id="1fc06-145">Klikněte pravým tlačítkem myši na uzel **ladění** a vyberte **Aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="1fc06-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="1fc06-146">Události trasování by měly být viditelné v prostředním podokně.</span><span class="sxs-lookup"><span data-stu-id="1fc06-146">Tracing events should be visible in the center pane.</span></span>

<span data-ttu-id="1fc06-147">WF 4 poskytuje sledování účastníka, který zapisuje záznamy sledování do relace ETW (Event Tracing for Windows).</span><span class="sxs-lookup"><span data-stu-id="1fc06-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="1fc06-148">Účastník sledování ETW je nakonfigurován s profilem sledování k odběru záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="1fc06-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span> <span data-ttu-id="1fc06-149">Je-li povoleno sledování, jsou e-tW emitovány záznamy sledování chyb.</span><span class="sxs-lookup"><span data-stu-id="1fc06-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="1fc06-150">Události sledování ETW (mezi rozsahem 100-113) odpovídající událostem sledování vyzařovaným účastníkem sledování ETW jsou zapsány do analytického protokolu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>

<span data-ttu-id="1fc06-151">Chcete-li zobrazit záznamy sledování, postupujte takto.</span><span class="sxs-lookup"><span data-stu-id="1fc06-151">To view tracking records, follow these steps.</span></span>

1. <span data-ttu-id="1fc06-152">Pokud chcete spustit Prohlížeč událostí, klikněte na **Tlačítko Start**a potom klikněte na **Spustit.**</span><span class="sxs-lookup"><span data-stu-id="1fc06-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="1fc06-153">V dialogovém okně `eventvwr`Spustit zadejte .</span><span class="sxs-lookup"><span data-stu-id="1fc06-153">In the Run dialog, type `eventvwr`.</span></span>

2. <span data-ttu-id="1fc06-154">V dialogovém okně Prohlížeč událostí rozbalte uzel **Protokoly aplikací a služeb.**</span><span class="sxs-lookup"><span data-stu-id="1fc06-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>

3. <span data-ttu-id="1fc06-155">Rozbalte uzly **Microsoft**, **Windows**a **Application Server-Applications.**</span><span class="sxs-lookup"><span data-stu-id="1fc06-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>

4. <span data-ttu-id="1fc06-156">Klepněte pravým tlačítkem myši na uzel **Analytická** analýza pod uzlemi **Aplikační server-aplikace** a vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="1fc06-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>

5. <span data-ttu-id="1fc06-157">Spusťte aplikaci s povolenou sledováním a vygenerujte záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="1fc06-157">Execute your tracking-enabled application to generate tracking records.</span></span>

6. <span data-ttu-id="1fc06-158">Klikněte pravým tlačítkem myši na uzel **Analytická** a vyberte **Aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="1fc06-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="1fc06-159">Záznamy sledování by měly být viditelné v prostředním podokně.</span><span class="sxs-lookup"><span data-stu-id="1fc06-159">Tracking records should be visible in the center pane.</span></span>

<span data-ttu-id="1fc06-160">Následující obrázek znázorňuje sledování událostí v prohlížeči událostí:</span><span class="sxs-lookup"><span data-stu-id="1fc06-160">The following image shows tracking events in the event viewer:</span></span>

![Snímek obrazovky prohlížeče událostí zobrazující záznamy sledování](./media/configuring-tracking-for-a-workflow/tracking-event-viewer.png)

### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="1fc06-162">Registrace ID poskytovatele specifického pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="1fc06-162">Registering an application-specific provider ID</span></span>

<span data-ttu-id="1fc06-163">Pokud události je třeba zapsat do protokolu konkrétní aplikace, postupujte takto zaregistrovat manifest nového zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="1fc06-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>

1. <span data-ttu-id="1fc06-164">Deklarujte ID zprostředkovatele v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1fc06-164">Declare the provider ID in the application configuration file.</span></span>

    ```xml
    <system.serviceModel>
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>
    </system.serviceModel>
    ```

2. <span data-ttu-id="1fc06-165">Zkopírujte soubor manifestu z %windir%\Microsoft.NET\Framework\\\<nejnovější verze [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man do dočasného umístění a přejmenujte jej na Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span><span class="sxs-lookup"><span data-stu-id="1fc06-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>

3. <span data-ttu-id="1fc06-166">Změňte identifikátor GUID v souboru manifestu na nový identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="1fc06-166">Change the GUID in the manifest file to the new GUID.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

4. <span data-ttu-id="1fc06-167">Pokud nechcete odinstalovat výchozího zprostředkovatele, změňte název zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="1fc06-167">Change the provider name if you do not want to uninstall the default provider.</span></span>

    ```xml
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" />
    ```

5. <span data-ttu-id="1fc06-168">Pokud jste v předchozím kroku změnili název zprostředkovatele, změňte názvy kanálů v souboru manifestu na nový název zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="1fc06-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>

    ```xml
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />
    ```

6. <span data-ttu-id="1fc06-169">Vygenerujte dll prostředku podle následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="1fc06-169">Generate the resource DLL by following these steps.</span></span>

    1. <span data-ttu-id="1fc06-170">Nainstalujte sadu Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="1fc06-170">Install the Windows SDK.</span></span> <span data-ttu-id="1fc06-171">Sada Windows SDK obsahuje kompilátor zpráv ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) a kompilátor prostředků ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span><span class="sxs-lookup"><span data-stu-id="1fc06-171">The Windows SDK includes the message compiler ([mc.exe](/windows/win32/wes/message-compiler--mc-exe-)) and resource compiler ([rc.exe](/windows/win32/menurc/using-rc-the-rc-command-line-)).</span></span>

    2. <span data-ttu-id="1fc06-172">V příkazovém řádku sady Windows SDK spusťte program mc.exe v novém souboru manifestu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>

        ```console
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

    3. <span data-ttu-id="1fc06-173">Spusťte soubor rc.exe v souboru prostředků generovaném v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="1fc06-173">Run rc.exe on the resource file generated in the previous step.</span></span>

        ```console
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc
        ```

    4. <span data-ttu-id="1fc06-174">Vytvořte prázdný cs soubor s názvem NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="1fc06-174">Create an empty cs file called NewProviderReg.cs.</span></span>

    5. <span data-ttu-id="1fc06-175">Vytvořte dll prostředku pomocí kompilátoru Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="1fc06-175">Create a resource DLL using the C# compiler.</span></span>

        ```console
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll
        ```

    6. <span data-ttu-id="1fc06-176">Změňte název dll prostředku a zprávy `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` v souboru manifestu z nového názvu dll.</span><span class="sxs-lookup"><span data-stu-id="1fc06-176">Change the resource and message dll name in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>

        ```xml
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" />
        ```

    7. <span data-ttu-id="1fc06-177">Použijte [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) k registraci manifestu.</span><span class="sxs-lookup"><span data-stu-id="1fc06-177">Use [wevtutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732848(v=ws.10)) to register the manifest.</span></span>

        ```console
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man
        ```

## <a name="see-also"></a><span data-ttu-id="1fc06-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fc06-178">See also</span></span>

- <span data-ttu-id="1fc06-179">[Monitorování prostředků infrastruktury aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1fc06-179">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="1fc06-180">[Monitorování aplikací pomocí prostředků infrastruktury aplikací](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1fc06-180">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
