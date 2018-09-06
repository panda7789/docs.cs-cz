---
title: Sledování profily
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 6651b79a474125f57c1cad773ae858dc7654d58a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861829"
---
# <a name="tracking-profiles"></a><span data-ttu-id="749c6-102">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="749c6-102">Tracking Profiles</span></span>
<span data-ttu-id="749c6-103">Sledování profily obsahuje sledování dotazy, které umožňují sledování účastník přihlásit k odběru události pracovních postupů, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="749c6-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>  
  
## <a name="tracking-profiles"></a><span data-ttu-id="749c6-104">Sledování profily</span><span class="sxs-lookup"><span data-stu-id="749c6-104">Tracking Profiles</span></span>  
 <span data-ttu-id="749c6-105">Sledování profily se používají k určení, jaké informace o sledování je vygenerován pro instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="749c6-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="749c6-106">Pokud není zadán žádný profil, jsou emitovány všechny události sledování.</span><span class="sxs-lookup"><span data-stu-id="749c6-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="749c6-107">Pokud je zadaný profil, bude vygenerován sledování událostí specifikovaný v profilu.</span><span class="sxs-lookup"><span data-stu-id="749c6-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="749c6-108">V závislosti na vašich požadavků na monitorování napíšete profilu, který je velmi obecná, který se přihlásí k odběru malou sadu změn stavu vysoké úrovně v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="749c6-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="749c6-109">Naopak můžete vytvořit profil velmi podrobné, jehož výsledné události jsou bohaté dostatečně k rekonstrukci podrobné provádění toku později.</span><span class="sxs-lookup"><span data-stu-id="749c6-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="749c6-110">Sledování profily projevují jako XML elementů v rámci standardní [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] konfigurační soubor nebo zadaný v kódu.</span><span class="sxs-lookup"><span data-stu-id="749c6-110">Tracking profiles manifest themselves as XML elements within a standard [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration file or specified in code.</span></span> <span data-ttu-id="749c6-111">V následujícím příkladu je [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profil sledování tracking profile v konfiguračním souboru, který umožňuje sledování účastník přihlásit k odběru `Started` a `Completed` události pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="749c6-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <tracking>    
      <trackingProfile name="Sample Tracking Profile">  
        <workflow activityDefinitionId="*">  
          <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                <state name="Started"/>  
                <state name="Completed"/>  
              </states>  
            </workflowInstanceQuery>  
          </workflowInstanceQueries>  
        </workflow>  
      </trackingProfile>          
    </profiles>  
  </tracking>  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="749c6-112">Následující příklad ukazuje ekvivalent sledování profil se vytvořil pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="749c6-112">The following example shows the equivalent tracking profile created using code.</span></span>  
  
```csharp  
TrackingProfile profile = new TrackingProfile()  
{  
    Name = "CustomTrackingProfile",  
    Queries =   
    {  
        new WorkflowInstanceQuery()  
        {  
            // Limit workflow instance tracking records for started and  
            // completed workflow states.  
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },  
        }  
    }  
};  
```  
  
 <span data-ttu-id="749c6-113">Sledování záznamy jsou filtrovány pomocí režim viditelnosti v rámci profilu sledování používání <xref:System.Activities.Tracking.ImplementationVisibility> atribut.</span><span class="sxs-lookup"><span data-stu-id="749c6-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="749c6-114">Složená aktivita je nejvyšší úrovně aktivity, který obsahuje další aktivity, které tvoří jeho implementace.</span><span class="sxs-lookup"><span data-stu-id="749c6-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="749c6-115">Určuje režim viditelnosti záznamů sledování vyzařováno složených aktivit v rámci aktivity pracovního postupu, chcete-li určit, pokud jsou sledovány aktivity, které tvoří implementaci.</span><span class="sxs-lookup"><span data-stu-id="749c6-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span>  <span data-ttu-id="749c6-116">Režim viditelnosti se vztahuje na sledování profil úroveň.</span><span class="sxs-lookup"><span data-stu-id="749c6-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="749c6-117">Filtrování sledování záznamů pro jednotlivé aktivity v pracovním postupu je řízen pomocí dotazů v rámci profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="749c6-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="749c6-118">Další informace najdete v tématu **sledování typů profilů dotazu** části v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="749c6-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>  
  
 <span data-ttu-id="749c6-119">Viditelnost dva režimy určené `implementationVisibility` atributu v profilu sledování `RootScope` a `All`.</span><span class="sxs-lookup"><span data-stu-id="749c6-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="749c6-120">Použití `RootScope` režimu potlačí na sledování záznamy aktivity, které tvoří implementaci aktivity v případě, kdy složené aktivity není kořenem pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="749c6-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span>  <span data-ttu-id="749c6-121">Z toho vyplývá, že když aktivita, která je implementována pomocí další aktivity se přidá do pracovního postupu a `implementationVisibility` nastavíte RootScope, jsou sledovány pouze nejvyšší úrovně aktivity v rámci složené aktivity.</span><span class="sxs-lookup"><span data-stu-id="749c6-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="749c6-122">Pokud aktivita je kořenového pracovního postupu, je provádění aktivity pracovního postupu pro aktivity, které tvoří implementaci jsou emitovány samostatně a sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="749c6-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="749c6-123">Všechny režimu povoluje všechny záznamy sledování, aby byly vypuštěny kořenové aktivity a všechny složené aktivity.</span><span class="sxs-lookup"><span data-stu-id="749c6-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>  
  
 <span data-ttu-id="749c6-124">Předpokládejme například, že *MyActivity* je složená aktivita, jejíž implementace obsahuje dvě aktivity *aktivity "activity1"* a *"activity2"*.</span><span class="sxs-lookup"><span data-stu-id="749c6-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span>  <span data-ttu-id="749c6-125">Když je tato aktivita přidána do pracovního postupu a je povoleno sledování pomocí profilu sledování s `implementationVisibility` nastavena na `RootScope`, jsou vydávány sledování záznamů pouze pro *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="749c6-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span>  <span data-ttu-id="749c6-126">Nicméně jsou emitovány žádné záznamy pro aktivity *aktivity "activity1"* a *"activity2"*.</span><span class="sxs-lookup"><span data-stu-id="749c6-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="749c6-127">Ale pokud `implementationVisisbility` atribut profilu sledování je nastavený na `All`, pak jsou vydávány sledování záznamů nejen *MyActivity*, ale také pro aktivity *aktivity "activity1"* a  *"Activity2"*.</span><span class="sxs-lookup"><span data-stu-id="749c6-127">However, if the `implementationVisisbility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>  
  
 <span data-ttu-id="749c6-128">`implementationVisibility` Příznak platí pro následující typy záznamů sledování:</span><span class="sxs-lookup"><span data-stu-id="749c6-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>  
  
-   <span data-ttu-id="749c6-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="749c6-129">ActivityStateRecord</span></span>  
  
-   <span data-ttu-id="749c6-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="749c6-130">FaultPropagationRecord</span></span>  
  
-   <span data-ttu-id="749c6-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="749c6-131">CancelRequestedRecord</span></span>  
  
-   <span data-ttu-id="749c6-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="749c6-132">ActivityScheduledRecord</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="749c6-133">Nastavením implementationVisibility nejsou odfiltrovat CustomTrackingRecords vyzařováno implementaci aktivity.</span><span class="sxs-lookup"><span data-stu-id="749c6-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>  
  
 <span data-ttu-id="749c6-134">`implementationVisibility` Funkce je zadán jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> na sledování profil v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="749c6-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>  
  
```  
TrackingProfile sampleTrackingProfile = new TrackingProfile()  
{  
    Name = "Sample Tracking Profile",  
    ImplementationVisibility = ImplementationVisibility.RootScope  
};  
```  
  
 <span data-ttu-id="749c6-135">`implementationVisibility` Funkce je zadán jako <xref:System.Activities.Tracking.ImplementationVisibility.All> profilu sledování v konfiguraci souboru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="749c6-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>  
  
```xml  
<tracking>  
      <profiles>  
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">  
          <workflow activityDefinitionId="*">  
...  
         </workflow>  
        </trackingProfile>  
      </profiles>  
</tracking>  
```  
  
 <span data-ttu-id="749c6-136">`ImplementationVisibility` Je volitelné nastavení v profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="749c6-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="749c6-137">Ve výchozím nastavení, jeho hodnota nastavená na `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="749c6-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="749c6-138">Hodnoty pro tento atribut se také malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="749c6-138">The values for this attribute are also case-sensitive.</span></span>  
  
### <a name="tracking-profile-query-types"></a><span data-ttu-id="749c6-139">Typy dotazů profilu sledování</span><span class="sxs-lookup"><span data-stu-id="749c6-139">Tracking Profile Query Types</span></span>  
 <span data-ttu-id="749c6-140">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="749c6-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="749c6-141">Existuje několik typů dotazu, které umožňují předplatit různé třídy <xref:System.Activities.Tracking.TrackingRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="749c6-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="749c6-142">Sledování profily se dá nastavit v konfiguraci nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="749c6-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="749c6-143">Tady jsou nejčastější typy dotazů:</span><span class="sxs-lookup"><span data-stu-id="749c6-143">Here are the most common query types:</span></span>  
  
-   <span data-ttu-id="749c6-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> – Můžete tak sledovat změny životního cyklu instance pracovního postupu jako dříve-jsme vám ukázali `Started` a `Completed`.</span><span class="sxs-lookup"><span data-stu-id="749c6-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="749c6-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="749c6-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
    -   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
     <span data-ttu-id="749c6-146">Stavy, které se můžete přihlásit k odběru jsou uvedeny v <xref:System.Activities.Tracking.WorkflowInstanceStates> třídy.</span><span class="sxs-lookup"><span data-stu-id="749c6-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>  
  
     <span data-ttu-id="749c6-147">Konfigurace nebo kódu používá k odběru na úrovni instance sledování záznamů pro pracovní postup `Started` pomocí stav instance <xref:System.Activities.Tracking.WorkflowInstanceQuery> je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="749c6-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <workflowInstanceQueries>  
        <workflowInstanceQuery>  
          <states>  
            <state name="Started"/>  
          </states>  
        </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new WorkflowInstanceQuery()  
            {  
                States = { WorkflowInstanceStates.Started}                                                                     
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="749c6-148"><xref:System.Activities.Tracking.ActivityStateQuery> – Tuto možnost použijte sledování změn životního cyklu aktivit, které tvoří instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="749c6-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="749c6-149">Můžete například sledovat, pokaždé, když dokončí "Odeslat E-Mail" aktivity v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="749c6-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="749c6-150">Tento dotaz je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.ActivityStateRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="749c6-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="749c6-151">Dostupné stavy přihlásit k odběru jsou uvedeny v <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="749c6-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>  
  
     <span data-ttu-id="749c6-152">Konfigurace a kód používá k registraci záznamů o sledování stavu aktivity, které používají <xref:System.Activities.Tracking.ActivityStateQuery> pro `SendEmailActivity` aktivity je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="749c6-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>  
  
    ```xml  
    <activityStateQueries>  
      <activityStateQuery activityName="SendEmailActivity">  
        <states>  
          <state name="Closed"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new ActivityStateQuery()  
            {                              
                ActivityName = "SendEmailActivity",  
                States = { ActivityStates.Closed }  
            }  
        }  
    };  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="749c6-153">Pokud více activityStateQuery elementy mají stejný název, stavy v posledním elementu se používají v profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="749c6-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>  
  
-   <span data-ttu-id="749c6-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> – Tento dotaz můžete ke sledování aktivitu naplánovat provedení podle aktivity jako nadřazený.</span><span class="sxs-lookup"><span data-stu-id="749c6-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="749c6-155">Dotaz, je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.ActivityScheduledRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="749c6-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>  
  
     <span data-ttu-id="749c6-156">Konfigurace a kód používaný k přihlásit k odběru záznamů související s `SendEmailActivity` podřízená aktivita naplánované pomocí <xref:System.Activities.Tracking.ActivityScheduledQuery> je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="749c6-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <activityScheduledQueries>  
      <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
     </activityScheduledQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new ActivityScheduledQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="749c6-157"><xref:System.Activities.Tracking.FaultPropagationQuery> – Použijte to ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="749c6-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="749c6-158">Dotaz, je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.FaultPropagationRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="749c6-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>  
  
     <span data-ttu-id="749c6-159">Konfigurace a kód používaný k přihlásit k odběru záznamů související s pomocí šíření chyb <xref:System.Activities.Tracking.FaultPropagationQuery> je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="749c6-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <faultPropagationQueries>  
      <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />  
    </faultPropagationQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =  
        {  
            new FaultPropagationQuery()  
            {  
                FaultSourceActivityName = "SendEmailActivity",  
                FaultHandlerActivityName = "NotificationsFaultHandler"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="749c6-160"><xref:System.Activities.Tracking.CancelRequestedQuery> – Použijte to ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="749c6-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="749c6-161">Dotaz, je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.CancelRequestedRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="749c6-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>  
  
     <span data-ttu-id="749c6-162">Konfigurace a kód používaný k přihlásit k odběru záznamů týkající se použití aktivity zrušení <xref:System.Activities.Tracking.CancelRequestedQuery> je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="749c6-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <cancelRequestedQueries>  
      <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />  
    </cancelRequestedQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CancelRequestedQuery()  
            {  
                ActivityName = "ProcessNotificationsActivity",  
                ChildActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="749c6-163"><xref:System.Activities.Tracking.CustomTrackingQuery> – Tuto možnost použijte sledování událostí, které definujete své kód aktivity.</span><span class="sxs-lookup"><span data-stu-id="749c6-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="749c6-164">Dotaz, je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.CustomTrackingRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="749c6-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>  
  
     <span data-ttu-id="749c6-165">Konfigurace a kód používaný k přihlásit k odběru záznamů související s vlastní sledování záznamů pomocí <xref:System.Activities.Tracking.CustomTrackingQuery> je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="749c6-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <customTrackingQueries>  
      <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />  
    </customTrackingQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new CustomTrackingQuery()   
            {  
                Name = "EmailAddress",  
                ActivityName = "SendEmailActivity"  
            }  
        }  
    };  
    ```  
  
-   <span data-ttu-id="749c6-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> – Použijte to ke sledování obnovení záložku v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="749c6-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="749c6-167">Tento dotaz je nezbytné pro <xref:System.Activities.Tracking.TrackingParticipant> přihlásit k odběru <xref:System.Activities.Tracking.BookmarkResumptionRecord> objekty.</span><span class="sxs-lookup"><span data-stu-id="749c6-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>  
  
     <span data-ttu-id="749c6-168">Konfigurace a kód používaný k přihlásit k odběru záznamů týkající se použití obnovení záložku <xref:System.Activities.Tracking.BookmarkResumptionQuery> je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="749c6-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>  
  
    ```xml  
    <bookmarkResumptionQueries>  
      <bookmarkResumptionQuery name="SentEmailBookmark" />  
    </bookmarkResumptionQueries>  
    ```  
  
    ```  
    TrackingProfile sampleTrackingProfile = new TrackingProfile()  
    {  
        Name = "Sample Tracking Profile",  
        Queries =   
        {  
            new BookmarkResumptionQuery()  
            {  
                Name = "sentEmailBookmark"  
            }  
        }  
    };  
    ```  
  
### <a name="annotations"></a><span data-ttu-id="749c6-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="749c6-169">Annotations</span></span>  
 <span data-ttu-id="749c6-170">Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení.</span><span class="sxs-lookup"><span data-stu-id="749c6-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="749c6-171">Například chtít několik sledování záznamů napříč několika pracovních úloh a být s klíčovým slovem "Poštovního serveru" == "Pošty Server1".</span><span class="sxs-lookup"><span data-stu-id="749c6-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="749c6-172">To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.</span><span class="sxs-lookup"><span data-stu-id="749c6-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
 <span data-ttu-id="749c6-173">K tomu, poznámka přidána do dotazu sledování, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="749c6-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="749c6-174">Postup vytvoření profilu sledování</span><span class="sxs-lookup"><span data-stu-id="749c6-174">How to Create a Tracking Profile</span></span>  
 <span data-ttu-id="749c6-175">Sledování elementy dotazu se používají k vytvoření profilu sledování pomocí konfiguračního souboru XML nebo [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]kódu.</span><span class="sxs-lookup"><span data-stu-id="749c6-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]code.</span></span>  <span data-ttu-id="749c6-176">Tady je příklad profilu sledování vytvořené pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="749c6-176">Here is an example of a tracking profile created using a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <tracking>  
    <profiles>  
      <trackingProfile name="Sample Tracking Profile ">  
        <workflow activityDefinitionId="*">  
          <!--Specify the tracking profile query elements to subscribe for tracking records-->  
        </workflow>  
      </trackingProfile>  
    </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
> [!WARNING]
>  <span data-ttu-id="749c6-177">WF pomocí hostitele služby pracovního postupu se profilu sledování obvykle vytvoří pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="749c6-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="749c6-178">Je také možné vytvořit profil sledování s kódem pomocí profilu sledování a sledování rozhraní API pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="749c6-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>  
  
 <span data-ttu-id="749c6-179">Profil nakonfigurovaný jako soubor XML konfigurace platí pro sledování účastníka pomocí chování rozšíření.</span><span class="sxs-lookup"><span data-stu-id="749c6-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="749c6-180">Ten se přidává k hostiteli WorkflowServiceHost, jak je popsáno v další části [konfigurace sledování pracovního postupu](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="749c6-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
 <span data-ttu-id="749c6-181">Úroveň podrobností na sledování záznamy, protože ho vygeneroval hostitele se určuje podle nastavení konfigurace v rámci profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="749c6-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="749c6-182">Účastník sledování přihlásí k sledování záznamů tak, že přidáte dotazy sledovacího profilu.</span><span class="sxs-lookup"><span data-stu-id="749c6-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="749c6-183">Přihlásit k odběru všech sledování záznamů, musí určovat všechny dotazy sledování pomocí profilu sledování "\*" název pole v jednotlivých dotazů.</span><span class="sxs-lookup"><span data-stu-id="749c6-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>  
  
 <span data-ttu-id="749c6-184">Tady jsou některé běžné příklady sledování profilů.</span><span class="sxs-lookup"><span data-stu-id="749c6-184">Here are some of the common examples of tracking profiles.</span></span>  
  
-   <span data-ttu-id="749c6-185">Profil sledování získat záznamy instance pracovního postupu a chyb.</span><span class="sxs-lookup"><span data-stu-id="749c6-185">A tracking profile to obtain workflow instance records and faults.</span></span>  
  
```xml  
<trackingProfile name="Instance and Fault Records">  
  <workflow activityDefinitionId="*">  
    <workflowInstanceQueries>  
      <workflowInstanceQuery>  
        <states>  
          <state name="*" />  
        </states>  
      </workflowInstanceQuery>  
    </workflowInstanceQueries>  
    <activityStateQueries>  
      <activityStateQuery activityName="*">  
        <states>  
          <state name="Faulted"/>  
        </states>  
      </activityStateQuery>  
    </activityStateQueries>  
  </workflow>  
</trackingProfile>  
```  
  
1.  <span data-ttu-id="749c6-186">Profil sledování získat všechny vlastní sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="749c6-186">A tracking profile to obtain all custom tracking records.</span></span>  
  
```xml  
<trackingProfile name="Instance_And_Custom_Records">  
  <workflow activityDefinitionId="*">  
    <customTrackingQueries>  
      <customTrackingQuery name="*" activityName="*" />  
    </customTrackingQueries>  
  </workflow>  
</trackingProfile>  
```  
  
## <a name="see-also"></a><span data-ttu-id="749c6-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="749c6-187">See Also</span></span>  
 [<span data-ttu-id="749c6-188">Sledování SQL</span><span class="sxs-lookup"><span data-stu-id="749c6-188">SQL Tracking</span></span>](../../../docs/framework/windows-workflow-foundation/samples/sql-tracking.md)  
 [<span data-ttu-id="749c6-189">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="749c6-189">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="749c6-190">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="749c6-190">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
