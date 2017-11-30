---
title: "Konfigurace sledování pro pracovní postup"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 905adcc9-30a0-4918-acd6-563f86db988a
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: abc935da740f68006855854fac26e9d209dcd53c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-tracking-for-a-workflow"></a><span data-ttu-id="759f0-102">Konfigurace sledování pro pracovní postup</span><span class="sxs-lookup"><span data-stu-id="759f0-102">Configuring Tracking for a Workflow</span></span>
<span data-ttu-id="759f0-103">Pracovní postup můžete provést třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="759f0-103">A workflow can execute in three ways:</span></span>  
  
-   <span data-ttu-id="759f0-104">Hostované v<xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="759f0-104">Hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
-   <span data-ttu-id="759f0-105">Provést, protože<xref:System.Activities.WorkflowApplication></span><span class="sxs-lookup"><span data-stu-id="759f0-105">Executed as a <xref:System.Activities.WorkflowApplication></span></span>  
  
-   <span data-ttu-id="759f0-106">Provést přímo pomocí<xref:System.Activities.WorkflowInvoker></span><span class="sxs-lookup"><span data-stu-id="759f0-106">Executed directly using <xref:System.Activities.WorkflowInvoker></span></span>  
  
 <span data-ttu-id="759f0-107">V závislosti na pracovním postupu možností hostování účastník sledování přidat kód nebo pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="759f0-107">Depending on the workflow hosting option, a tracking participant can be added either through code or through a configuration file.</span></span> <span data-ttu-id="759f0-108">Toto téma popisuje konfiguraci sledování přidáním sledování navrhnout <xref:System.Activities.WorkflowApplication> a <xref:System.ServiceModel.Activities.WorkflowServiceHost>a jak povolit sledování, pokud používáte <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="759f0-108">This topic describes how tracking is configured by adding a tracking participant to a <xref:System.Activities.WorkflowApplication> and to a <xref:System.ServiceModel.Activities.WorkflowServiceHost>, and how to enable tracking when using <xref:System.Activities.WorkflowInvoker>.</span></span>  
  
## <a name="configuring-workflow-application-tracking"></a><span data-ttu-id="759f0-109">Konfigurace aplikace pracovního postupu pro sledování</span><span class="sxs-lookup"><span data-stu-id="759f0-109">Configuring Workflow Application Tracking</span></span>  
 <span data-ttu-id="759f0-110">Pracovní postup můžete spustit pomocí <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="759f0-110">A workflow can run using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="759f0-111">Toto téma popisuje, jak je sledování nakonfigurovaná pro [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] aplikace pracovního postupu přidáním sledování navrhnout <xref:System.Activities.WorkflowApplication> hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="759f0-111">This topic demonstrates how tracking is configured for a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] workflow application by adding a tracking participant to the <xref:System.Activities.WorkflowApplication> workflow host.</span></span> <span data-ttu-id="759f0-112">V takovém případě pracovní postup spouští jako aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="759f0-112">In this case, the workflow runs as a workflow application.</span></span> <span data-ttu-id="759f0-113">Konfigurace aplikace pracovního postupu prostřednictvím kódu (nikoli pomocí konfiguračního souboru), což je vlastním hostováním .exe souboru pomocí <xref:System.Activities.WorkflowApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="759f0-113">You configure a workflow application through code (rather than by using a configuration file), which is a self-hosted .exe file using the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="759f0-114">Sledování účastník se přidal jako extension <xref:System.Activities.WorkflowApplication> instance.</span><span class="sxs-lookup"><span data-stu-id="759f0-114">The tracking participant is added as an extension to the <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="759f0-115">To se provádí přidáním <xref:System.Activities.Tracking.TrackingParticipant> ke kolekci rozšíření pro instanci WorkflowApplication.</span><span class="sxs-lookup"><span data-stu-id="759f0-115">This is done by adding the <xref:System.Activities.Tracking.TrackingParticipant> to the extensions collection for the WorkflowApplication instance.</span></span>  
  
 <span data-ttu-id="759f0-116">Aplikace pomocí pracovního postupu můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> chování rozšíření, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="759f0-116">For a workflow application, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension as shown in the following code.</span></span>  
  
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
  
### <a name="configuring-workflow-service-tracking"></a><span data-ttu-id="759f0-117">Konfigurace sledování služby pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="759f0-117">Configuring Workflow Service Tracking</span></span>  
 <span data-ttu-id="759f0-118">Pracovní postup, mohou být zpřístupněny jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby, když jsou hostované v <xref:System.ServiceModel.Activities.WorkflowServiceHost> hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="759f0-118">A workflow can be exposed as a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service when hosted in the <xref:System.ServiceModel.Activities.WorkflowServiceHost> service host.</span></span> <span data-ttu-id="759f0-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost>je specializovaná implementace rozhraní .NET ServiceHost služby založené na pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="759f0-119"><xref:System.ServiceModel.Activities.WorkflowServiceHost> is a specialized .NET ServiceHost implementation for a workflow-based service.</span></span> <span data-ttu-id="759f0-120">Tato část vysvětluje postup konfigurace sledování pro [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pracovního postupu služby spuštěné <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="759f0-120">This section explains how to configure tracking for a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow service running in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="759f0-121">Je nakonfigurovaný pomocí souboru Web.config (pro hostované webové služby) nebo soubor App.config (pro služby hostované v samostatná aplikace, jako je například aplikace konzoly) zadáním chování služby nebo prostřednictvím kódu přidáním specifické pro sledování chování <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekce hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="759f0-121">It is configured through a Web.config file (for a Web-hosted service) or an App.config file (for a service hosted in a stand-alone application, such as a console application) by specifying a service behavior or through code by adding a tracking-specific behavior to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection for the service host.</span></span>  
  
 <span data-ttu-id="759f0-122">Pro pracovní postup služby hostované v <xref:System.ServiceModel.WorkflowServiceHost>, můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> pomocí <`behavior`> element v konfiguračním souboru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="759f0-122">For a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile" />  
        </behavior>              
   </serviceBehaviors>  
<behaviors>  
```  
  
 <span data-ttu-id="759f0-123">Můžete taky pro pracovní postup služby hostované v <xref:System.ServiceModel.WorkflowServiceHost>, můžete přidat <xref:System.Activities.Tracking.EtwTrackingParticipant> chování rozšíření prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="759f0-123">Alternatively, for a workflow service hosted in <xref:System.ServiceModel.WorkflowServiceHost>, you can add the <xref:System.Activities.Tracking.EtwTrackingParticipant> behavior extension through code.</span></span> <span data-ttu-id="759f0-124">Pokud chcete přidat vlastní sledování účastník, vytvořte nové rozšíření chování a přidejte ho do <xref:System.ServiceModel.ServiceHost> jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="759f0-124">To add a custom tracking participant, create a new behavior extension and add it to the <xref:System.ServiceModel.ServiceHost> as shown in the following example code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="759f0-125">Pokud chcete zobrazit ukázkový kód, který ukazuje, jak vytvořit vlastní chování element, který přidá vlastní sledování účastník, podívejte se na [sledování](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) ukázky.</span><span class="sxs-lookup"><span data-stu-id="759f0-125">If you want to view sample code that shows how to create a custom behavior element that adds a custom tracking participant, refer to the [Tracking](../../../docs/framework/windows-workflow-foundation/samples/tracking.md) samples.</span></span>  
  
```  
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
  
 <span data-ttu-id="759f0-126">Sledování účastník je na hostiteli služby pracovního postupu přidal jako extension v chování.</span><span class="sxs-lookup"><span data-stu-id="759f0-126">The tracking participant is added to the workflow service host as an extension to the behavior.</span></span>  
  
 <span data-ttu-id="759f0-127">Následující ukázkový kód ukazuje, jak načíst profil sledování z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="759f0-127">This sample code below shows how to read a tracking profile from configuration file.</span></span>  
  
```  
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
  
 <span data-ttu-id="759f0-128">Tento ukázkový kód ukazuje, jak přidat profil sledování do hostitele pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="759f0-128">This sample code shows how to add a tracking profile to a workflow host.</span></span>  
  
```  
WorkflowServiceHost workflowServiceHost = serviceHostBase as WorkflowServiceHost;  
if (null != workflowServiceHost)  
{  
              string workflowDisplayName = workflowServiceHost.Activity.DisplayName;  
               TrackingProfile trackingProfile = GetProfile(this.profileName, workflowDisplayName);  
                workflowServiceHost.WorkflowExtensions.Add(()  => new EtwTrackingParticipant  {  
               TrackingProfile = trackingProfile  
                        });  
 }  
```  
  
> [!NOTE]
>  <span data-ttu-id="759f0-129">Další informace o sledování profily, najdete v části [sledování profily](http://go.microsoft.com/fwlink/?LinkId=201310).</span><span class="sxs-lookup"><span data-stu-id="759f0-129">For more information on tracking profiles, refer to [Tracking Profiles](http://go.microsoft.com/fwlink/?LinkId=201310).</span></span>  
  
### <a name="configuring-tracking-using-workflowinvoker"></a><span data-ttu-id="759f0-130">Konfigurace sledování pomocí WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="759f0-130">Configuring tracking using WorkflowInvoker</span></span>  
 <span data-ttu-id="759f0-131">Konfigurace sledování pro pracovní postup provést pomocí <xref:System.Activities.WorkflowInvoker>, přidejte zprostředkovatele sledování jako rozšíření <xref:System.Activities.WorkflowInvoker> instance.</span><span class="sxs-lookup"><span data-stu-id="759f0-131">To configure tracking for a workflow executed using <xref:System.Activities.WorkflowInvoker>, add the tracking provider as an extension to a <xref:System.Activities.WorkflowInvoker> instance.</span></span> <span data-ttu-id="759f0-132">Následující příklad kódu je z [vlastní sledování](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="759f0-132">The following code example is from the [Custom Tracking](../../../docs/framework/windows-workflow-foundation/samples/custom-tracking.md) sample.</span></span>  
  
```  
WorkflowInvoker invoker = new WorkflowInvoker(BuildSampleWorkflow());  
invoker.Extensions.Add(customTrackingParticipant);  
invoker.Invoke();  
```  
  
### <a name="viewing-tracking-records-in-event-viewer"></a><span data-ttu-id="759f0-133">Zobrazení sledování záznamů v prohlížeči událostí</span><span class="sxs-lookup"><span data-stu-id="759f0-133">Viewing tracking records in Event Viewer</span></span>  
 <span data-ttu-id="759f0-134">Existují dva protokoly Prohlížeče událostí zajímají hlavně o zobrazíte při sledování provádění WF - analytické protokolu a protokolu ladění.</span><span class="sxs-lookup"><span data-stu-id="759f0-134">There are two Event Viewer logs of particular interest to view when tracking WF execution - the Analytic log and the Debug log.</span></span> <span data-ttu-id="759f0-135">Obě jsou umístěny v části Microsoft &#124; Windows &#124; Aplikace serveru – aplikace uzlu.</span><span class="sxs-lookup"><span data-stu-id="759f0-135">Both reside under the Microsoft&#124;Windows&#124;Application Server-Applications node.</span></span>  <span data-ttu-id="759f0-136">Protokoly v této části obsahují události z jedné aplikace a nikoli události, které mají vliv na celý systém.</span><span class="sxs-lookup"><span data-stu-id="759f0-136">Logs within this section contain events from a single application rather than events that have an impact on the entire system.</span></span>  
  
 <span data-ttu-id="759f0-137">Ladění trasování, které události se zapisují do protokolů ladění.</span><span class="sxs-lookup"><span data-stu-id="759f0-137">Debug trace events are written to the Debug Log.</span></span> <span data-ttu-id="759f0-138">Chcete-li shromažďovat události trasování ladění WF v prohlížeči událostí, povolte protokol ladění.</span><span class="sxs-lookup"><span data-stu-id="759f0-138">To collect WF debug trace events in the Event Viewer, enable the Debug Log.</span></span>  
  
1.  <span data-ttu-id="759f0-139">Chcete-li spustit nástroj Prohlížeč událostí, klikněte na tlačítko **spustit**a pak klikněte na tlačítko **spustit.**</span><span class="sxs-lookup"><span data-stu-id="759f0-139">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="759f0-140">V dialogovém okně Spustit zadejte `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="759f0-140">In the Run dialog, type `eventvwr`.</span></span>  
  
2.  <span data-ttu-id="759f0-141">V dialogovém okně prohlížeče událostí, rozbalte **protokoly aplikací a služeb** uzlu.</span><span class="sxs-lookup"><span data-stu-id="759f0-141">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>  
  
3.  <span data-ttu-id="759f0-142">Rozbalte **Microsoft**, **Windows**, a **serveru aplikace – aplikace** uzlů.</span><span class="sxs-lookup"><span data-stu-id="759f0-142">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>  
  
4.  <span data-ttu-id="759f0-143">Klikněte pravým tlačítkem myši **ladění** pod uzlem **serveru aplikace – aplikace** uzel a vyberte možnost **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="759f0-143">Right-click the **Debug** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>  
  
5.  <span data-ttu-id="759f0-144">Spusťte aplikaci povoleno trasování generovat události trasování.</span><span class="sxs-lookup"><span data-stu-id="759f0-144">Execute your tracing-enabled application to generate tracing events.</span></span>  
  
6.  <span data-ttu-id="759f0-145">Klikněte pravým tlačítkem myši **ladění** uzel a vyberte možnost **aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="759f0-145">Right-click the **Debug** node and select **Refresh.**</span></span> <span data-ttu-id="759f0-146">Trasování událostí má být zobrazen ve středovém podokně.</span><span class="sxs-lookup"><span data-stu-id="759f0-146">Tracing events should be visible in the center pane.</span></span>  
  
 <span data-ttu-id="759f0-147">WF 4 poskytuje sledování člena, který zapíše sledování záznamů relaci trasování událostí pro Windows (trasování událostí pro Windows).</span><span class="sxs-lookup"><span data-stu-id="759f0-147">WF 4 provides a tracking participant that writes tracking records to an ETW (Event Tracing for Windows) session.</span></span> <span data-ttu-id="759f0-148">Trasování událostí pro Windows Sledování účastník je nakonfigurovaný s profil sledování k odběru sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="759f0-148">The ETW tracking participant is configured with a tracking profile to subscribe to tracking records.</span></span>  <span data-ttu-id="759f0-149">Pokud je povoleno sledování, jsou chyby sledování záznamy vygenerované do trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="759f0-149">When tracking is enabled, errors tracking records are emitted to ETW.</span></span> <span data-ttu-id="759f0-150">Trasování událostí pro Windows Sledování událostí (mezi rozsahu 100 113) odpovídající sledování události vygenerované účastníkem sledování, trasování událostí pro Windows se zapíšou do analytické protokolu.</span><span class="sxs-lookup"><span data-stu-id="759f0-150">ETW tracking events (between the range of 100-113) corresponding to the tracking events emitted by the ETW tracking participant are written to the Analytic Log.</span></span>  
  
 <span data-ttu-id="759f0-151">Chcete-li zobrazit záznamy o sledování, postupujte podle těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="759f0-151">To view tracking records, follow these steps.</span></span>  
  
1.  <span data-ttu-id="759f0-152">Chcete-li spustit nástroj Prohlížeč událostí, klikněte na tlačítko **spustit**a pak klikněte na tlačítko **spustit.**</span><span class="sxs-lookup"><span data-stu-id="759f0-152">To open Event Viewer, click **Start**, and then click **Run.**</span></span> <span data-ttu-id="759f0-153">V dialogovém okně Spustit zadejte `eventvwr`.</span><span class="sxs-lookup"><span data-stu-id="759f0-153">In the Run dialog, type `eventvwr`.</span></span>  
  
2.  <span data-ttu-id="759f0-154">V dialogovém okně prohlížeče událostí, rozbalte **protokoly aplikací a služeb** uzlu.</span><span class="sxs-lookup"><span data-stu-id="759f0-154">In the Event Viewer dialog, expand the **Applications and Services Logs** node.</span></span>  
  
3.  <span data-ttu-id="759f0-155">Rozbalte **Microsoft**, **Windows**, a **serveru aplikace – aplikace** uzlů.</span><span class="sxs-lookup"><span data-stu-id="759f0-155">Expand the **Microsoft**, **Windows**, and **Application Server-Applications** nodes.</span></span>  
  
4.  <span data-ttu-id="759f0-156">Klikněte pravým tlačítkem myši **analytické** pod uzlem **serveru aplikace – aplikace** uzel a vyberte možnost **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="759f0-156">Right-click the **Analytic** node under the **Application Server-Applications** node, and select **Enable Log**.</span></span>  
  
5.  <span data-ttu-id="759f0-157">Spuštění vaší aplikace s povolenými sledování ke generování sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="759f0-157">Execute your tracking-enabled application to generate tracking records.</span></span>  
  
6.  <span data-ttu-id="759f0-158">Klikněte pravým tlačítkem myši **analytické** uzel a vyberte možnost **aktualizovat.**</span><span class="sxs-lookup"><span data-stu-id="759f0-158">Right-click the **Analytic** node and select **Refresh.**</span></span> <span data-ttu-id="759f0-159">Sledování záznamy by měly jít vidět ve středovém podokně.</span><span class="sxs-lookup"><span data-stu-id="759f0-159">Tracking records should be visible in the center pane.</span></span>  
  
 <span data-ttu-id="759f0-160">Následující obrázek znázorňuje sledování událostí v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="759f0-160">The following image shows tracking events in the event viewer.</span></span>  
  
 <span data-ttu-id="759f0-161">![Zobrazuje Prohlížeč událostí sledování záznamů](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")</span><span class="sxs-lookup"><span data-stu-id="759f0-161">![Event Viewer showing tracking records](../../../docs/framework/windows-workflow-foundation/media/trackingeventviewer.PNG "TrackingEventViewer")</span></span>  
  
### <a name="registering-an-application-specific-provider-id"></a><span data-ttu-id="759f0-162">Registrace ID zprostředkovatele specifické pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="759f0-162">Registering an application-specific provider ID</span></span>  
 <span data-ttu-id="759f0-163">Pokud události jsou určeny k zápisu do protokolu konkrétní aplikaci, postupujte podle těchto kroků k registraci nového manifestu zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="759f0-163">If events need to be written to a specific application log, follow these steps to register the new provider manifest.</span></span>  
  
1.  <span data-ttu-id="759f0-164">Deklarujte ID zprostředkovatele v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="759f0-164">Declare the provider ID in the application configuration file.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <diagnostics etwProviderId="2720e974-9fe9-477a-bb60-81fe3bf91eec"/>  
    </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="759f0-165">Zkopírujte soubor manifestu z %windir%\Microsoft.NET\Framework\\< nejnovější verzi [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]> \Microsoft.Windows.ApplicationServer.Applications.man do dočasného umístění a přejmenujte ji na Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span><span class="sxs-lookup"><span data-stu-id="759f0-165">Copy the manifest file from %windir%\Microsoft.NET\Framework\\<latest version of [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]>\Microsoft.Windows.ApplicationServer.Applications.man to a temporary location, and rename it to Microsoft.Windows.ApplicationServer.Applications_Provider1.man</span></span>  
  
3.  <span data-ttu-id="759f0-166">Identifikátor GUID v souboru manifestu změňte na nový identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="759f0-166">Change the GUID in the manifest file to the new GUID.</span></span>  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
4.  <span data-ttu-id="759f0-167">Změňte název zprostředkovatele, pokud nechcete odinstalovat výchozího zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="759f0-167">Change the provider name if you do not want to uninstall the default provider.</span></span>  
  
    ```xml  
    <provider name="Microsoft-Windows-Application Server-Applications" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}"  
    ```  
  
5.  <span data-ttu-id="759f0-168">Pokud jste změnili název zprostředkovatele v předchozím kroku, změňte názvy kanál v souboru manifestu na nový název zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="759f0-168">If you changed the provider name in the previous step, change the channel names in the manifest file to the new provider name.</span></span>  
  
    ```xml  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Admin" chid="ADMIN_CHANNEL" symbol="ADMIN_CHANNEL" type="Admin" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ADMIN_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Operational" chid="OPERATIONAL_CHANNEL" symbol="OPERATIONAL_CHANNEL" type="Operational" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.OPERATIONAL_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Debug" chid="DEBUG_CHANNEL" symbol="DEBUG_CHANNEL" type="Debug" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.DEBUG_CHANNEL.message)" />  
    <channel name="Microsoft-Windows-Application Server-Applications_Provider1/Perf" chid="PERF_CHANNEL" symbol="PERF_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.PERF_CHANNEL.message)" />  
    ```  
  
6.  <span data-ttu-id="759f0-169">Generovat DLL prostředků pomocí následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="759f0-169">Generate the resource DLL by following these steps.</span></span>  
  
    1.  <span data-ttu-id="759f0-170">Instalace sady Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="759f0-170">Install the Windows SDK.</span></span> <span data-ttu-id="759f0-171">Sada Windows SDK zahrnuje kompilátoru zprávy ([mc.exe](http://go.microsoft.com/fwlink/?LinkId=184606)) a kompilátor prostředků ([rc.exe](http://go.microsoft.com/fwlink/?LinkId=184605)).</span><span class="sxs-lookup"><span data-stu-id="759f0-171">The Windows SDK includes the message compiler ([mc.exe](http://go.microsoft.com/fwlink/?LinkId=184606)) and resource compiler ([rc.exe](http://go.microsoft.com/fwlink/?LinkId=184605)).</span></span>  
  
    2.  <span data-ttu-id="759f0-172">V příkazovém řádku Windows SDK spusťte mc.exe na nový soubor manifestu.</span><span class="sxs-lookup"><span data-stu-id="759f0-172">In a Windows SDK command prompt, run mc.exe on the new manifest file.</span></span>  
  
        ```  
        mc.exe Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
    3.  <span data-ttu-id="759f0-173">Spusťte rc.exe v souboru prostředků vygenerované v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="759f0-173">Run rc.exe on the resource file generated in the previous step.</span></span>  
  
        ```  
        rc.exe  Microsoft.Windows.ApplicationServer.Applications_Provider1.rc  
        ```  
  
    4.  <span data-ttu-id="759f0-174">Vytvořte soubor prázdný cs názvem NewProviderReg.cs.</span><span class="sxs-lookup"><span data-stu-id="759f0-174">Create an empty cs file called NewProviderReg.cs.</span></span>  
  
    5.  <span data-ttu-id="759f0-175">Vytvořte prostředek knihovny DLL pomocí kompilátor jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="759f0-175">Create a resource DLL using the C# compiler.</span></span>  
  
        ```  
        csc /target:library /win32res:Microsoft.Windows.ApplicationServer.Applications_Provider1.res NewProviderReg.cs /out:Microsoft.Windows.ApplicationServer.Applications_Provider1.dll  
        ```  
  
    6.  <span data-ttu-id="759f0-176">Změnit dl namel prostředků a zpráv v souboru manifestu z `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` na nový název knihovny dll.</span><span class="sxs-lookup"><span data-stu-id="759f0-176">Change the resource and message dl namel in the manifest file from `Microsoft.Windows.ApplicationServer.Applications.Provider1.man` to the new dll name.</span></span>  
  
        ```xml  
        <provider name="Microsoft-Windows-Application Server-Applications_Provider1" guid="{2720e974-9fe9-477a-bb60-81fe3bf91eec}" symbol="Microsoft_Windows_ApplicationServer_ApplicationEvents" resourceFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll" messageFileName="<dll directory>\Microsoft.Windows.ApplicationServer.Applications_Provider1.dll">  
        ```  
  
    7.  <span data-ttu-id="759f0-177">Použití [wevtutil](http://go.microsoft.com/fwlink/?LinkId=184608) k registraci v manifestu.</span><span class="sxs-lookup"><span data-stu-id="759f0-177">Use [wevtutil](http://go.microsoft.com/fwlink/?LinkId=184608) to register the manifest.</span></span>  
  
        ```  
        wevtutil im Microsoft.Windows.ApplicationServer.Applications_Provider1.man  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="759f0-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="759f0-178">See Also</span></span>  
 [<span data-ttu-id="759f0-179">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="759f0-179">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="759f0-180">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="759f0-180">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
