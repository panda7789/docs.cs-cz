---
title: Sledování profilů
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9217f25ba4499e7ff75020642be387aa79ba27bf
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837620"
---
# <a name="tracking-profiles"></a><span data-ttu-id="b1c3f-102">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="b1c3f-102">Tracking Profiles</span></span>

<span data-ttu-id="b1c3f-103">Sledování profilů obsahuje sledovací dotazy, které umožňují sledování účastníka přihlásit k odběru událostí pracovního postupu, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="b1c3f-104">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="b1c3f-104">Tracking Profiles</span></span>

<span data-ttu-id="b1c3f-105">Sledování profilů se používá k určení, které informace o sledování budou vygenerovány pro instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="b1c3f-106">Pokud není zadán žádný profil, budou vygenerovány všechny události sledování.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="b1c3f-107">Pokud je zadán profil, budou vygenerovány události sledování zadané v profilu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="b1c3f-108">V závislosti na požadavcích na monitorování můžete napsat profil, který je velmi obecný, který se přihlásí k odběru malé sady změn stavu vysoké úrovně v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="b1c3f-109">Naopak můžete vytvořit velmi podrobný profil, jehož výsledné události jsou dostatečně bohatě pro pozdější vytvoření podrobného toku spuštění.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="b1c3f-110">Sledovací profily se manifestují jako prvky XML v rámci standardního konfiguračního souboru .NET Framework nebo jsou zadané v kódu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-110">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="b1c3f-111">V následujícím příkladu je profil sledování [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] v konfiguračním souboru, který umožňuje sledování účastníka přihlásit k odběru `Started` a `Completed` události pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

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

<span data-ttu-id="b1c3f-112">Následující příklad ukazuje ekvivalentní profil sledování vytvořený pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-112">The following example shows the equivalent tracking profile created using code.</span></span>

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

<span data-ttu-id="b1c3f-113">Sledování záznamů se filtruje přes režim viditelnosti v rámci profilu sledování pomocí atributu <xref:System.Activities.Tracking.ImplementationVisibility>.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="b1c3f-114">Složená aktivita je aktivita nejvyšší úrovně, která obsahuje další aktivity, které tvoří svou implementaci.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="b1c3f-115">Režim viditelnosti určuje sledování záznamů emitovaných ze složených aktivit v rámci aktivity pracovního postupu, které určují, jestli se mají sledovat aktivity, které tvoří implementaci.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="b1c3f-116">Režim viditelnosti se vztahuje na úroveň profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="b1c3f-117">Filtrování záznamů sledování pro jednotlivé aktivity v rámci pracovního postupu je řízeno dotazy v rámci profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="b1c3f-118">Další informace najdete v části **typy dotazů profilu sledování** v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="b1c3f-119">Dva režimy viditelnosti zadané atributem `implementationVisibility` v profilu sledování jsou `RootScope` a `All`.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="b1c3f-120">Použití režimu `RootScope` potlačí záznamy sledování pro aktivity, které tvoří implementaci aktivity v případě, že složená aktivita není kořenem pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="b1c3f-121">To znamená, že když se do pracovního postupu přidá aktivita, která je implementovaná pomocí jiných aktivit, a `implementationVisibility` nastavená na RootScope, bude sledována pouze aktivita nejvyšší úrovně v rámci této složené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="b1c3f-122">Pokud je aktivita kořenem pracovního postupu, pak implementace aktivity je samotný pracovní postup a záznamy sledování jsou vygenerovány pro aktivity, které tvoří implementaci.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="b1c3f-123">Použití režimu All povoluje generování všech záznamů sledování pro kořenovou aktivitu a všechny její složené aktivity.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="b1c3f-124">Předpokládejme například, že *MyActivity* je složená aktivita, jejíž implementace obsahuje dvě aktivity, *Activity1* a *"Activity2"* .</span><span class="sxs-lookup"><span data-stu-id="b1c3f-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="b1c3f-125">Když se tato aktivita přidá do pracovního postupu a sledování je povolené s profilem sledování s `implementationVisibility` nastavenou na `RootScope`, sledování záznamů se generuje jenom pro *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="b1c3f-126">Pro aktivity *Activity1* a *"Activity2"* se ale negenerují žádné záznamy.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="b1c3f-127">Pokud je však atribut `implementationVisibility` pro profil sledování nastaven na hodnotu `All`, pak sledování záznamů je generováno nejen pro *MyActivity*, ale také pro aktivity *Activity1* a *"Activity2"* .</span><span class="sxs-lookup"><span data-stu-id="b1c3f-127">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="b1c3f-128">Příznak `implementationVisibility` se vztahuje na následující typy záznamů sledování:</span><span class="sxs-lookup"><span data-stu-id="b1c3f-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="b1c3f-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="b1c3f-129">ActivityStateRecord</span></span>

- <span data-ttu-id="b1c3f-130">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="b1c3f-130">FaultPropagationRecord</span></span>

- <span data-ttu-id="b1c3f-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="b1c3f-131">CancelRequestedRecord</span></span>

- <span data-ttu-id="b1c3f-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="b1c3f-132">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="b1c3f-133">CustomTrackingRecords vysílaná z implementace aktivity není odfiltrována nastavením implementationVisibility.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="b1c3f-134">Funkce `implementationVisibility` je určena jako <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> v profilu sledování v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b1c3f-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="b1c3f-135">Funkce `implementationVisibility` je určena jako <xref:System.Activities.Tracking.ImplementationVisibility.All> v profilu sledování v konfiguračním souboru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b1c3f-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

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

<span data-ttu-id="b1c3f-136">Nastavení `ImplementationVisibility` v profilu sledování je volitelné.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="b1c3f-137">Ve výchozím nastavení je jeho hodnota nastavená na `RootScope`.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="b1c3f-138">Hodnoty pro tento atribut také rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-138">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="b1c3f-139">Typy dotazů na profil sledování</span><span class="sxs-lookup"><span data-stu-id="b1c3f-139">Tracking Profile Query Types</span></span>

<span data-ttu-id="b1c3f-140">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="b1c3f-141">Existuje několik typů dotazů, které umožňují přihlášení k odběru různých tříd <xref:System.Activities.Tracking.TrackingRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="b1c3f-142">Profily sledování lze zadat v konfiguraci nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="b1c3f-143">Tady jsou nejběžnější typy dotazů:</span><span class="sxs-lookup"><span data-stu-id="b1c3f-143">Here are the most common query types:</span></span>

- <span data-ttu-id="b1c3f-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> – Toto použijte ke sledování změn životního cyklu instance pracovního postupu, jako jsou dřív vykázáno `Started` a `Completed`.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="b1c3f-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="b1c3f-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="b1c3f-146">Stavy, které lze předplatit, jsou určeny ve třídě <xref:System.Activities.Tracking.WorkflowInstanceStates>.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="b1c3f-147">V následujícím příkladu je uvedena konfigurace nebo kód, který se používá k přihlášení k odběru záznamů sledování na úrovni instance pracovního postupu pro stav `Started` instance pomocí <xref:System.Activities.Tracking.WorkflowInstanceQuery>.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
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

- <span data-ttu-id="b1c3f-148"><xref:System.Activities.Tracking.ActivityStateQuery> – slouží ke sledování změn životního cyklu aktivit, které tvoří instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="b1c3f-149">Například můžete chtít sledovat pokaždé, když se aktivita odeslat E-Mail dokončí v instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="b1c3f-150">Tento dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.ActivityStateRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="b1c3f-151">Dostupné stavy pro přihlášení k odběru jsou určené v <xref:System.Activities.Tracking.ActivityStates>.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="b1c3f-152">V následujícím příkladu je uvedena konfigurace a kód, který se používá k odběru záznamů sledování stavu aktivity, které používají <xref:System.Activities.Tracking.ActivityStateQuery> pro aktivitu `SendEmailActivity`.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
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
  > <span data-ttu-id="b1c3f-153">Pokud má více elementů activityStateQuery stejný název, budou použity pouze stavy v posledním prvku v profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="b1c3f-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> – tento dotaz umožňuje sledovat aktivitu naplánovanou pro provádění nadřazenou aktivitou.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b1c3f-155">Dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.ActivityScheduledRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="b1c3f-156">V následujícím příkladu je uvedena konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s `SendEmailActivity` podřízená aktivita pomocí <xref:System.Activities.Tracking.ActivityScheduledQuery>.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
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

- <span data-ttu-id="b1c3f-157"><xref:System.Activities.Tracking.FaultPropagationQuery> – slouží ke sledování manipulace s chybami, ke kterým dojde v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="b1c3f-158">Dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.FaultPropagationRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="b1c3f-159">V následujícím příkladu je uvedena konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s šířením chyb pomocí <xref:System.Activities.Tracking.FaultPropagationQuery>.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
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

- <span data-ttu-id="b1c3f-160"><xref:System.Activities.Tracking.CancelRequestedQuery> – slouží ke sledování požadavků pro zrušení podřízené aktivity Nadřazená aktivita.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b1c3f-161">Dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.CancelRequestedRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="b1c3f-162">V následujícím příkladu je uvedena konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s zrušením aktivity pomocí <xref:System.Activities.Tracking.CancelRequestedQuery>.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
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

- <span data-ttu-id="b1c3f-163"><xref:System.Activities.Tracking.CustomTrackingQuery> – slouží ke sledování událostí, které definujete v aktivitách kódu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="b1c3f-164">Dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.CustomTrackingRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="b1c3f-165">Konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s vlastními záznamy sledování pomocí <xref:System.Activities.Tracking.CustomTrackingQuery>, je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
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

- <span data-ttu-id="b1c3f-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> – slouží ke sledování obnovování záložky v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="b1c3f-167">Tento dotaz je nutný, aby se <xref:System.Activities.Tracking.TrackingParticipant> přihlásil k odběru <xref:System.Activities.Tracking.BookmarkResumptionRecord> objektů.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="b1c3f-168">Konfigurace a kód, který se používá k přihlášení k odběru záznamů souvisejících s obnovením záložek pomocí <xref:System.Activities.Tracking.BookmarkResumptionQuery>, je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
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

### <a name="annotations"></a><span data-ttu-id="b1c3f-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1c3f-169">Annotations</span></span>

<span data-ttu-id="b1c3f-170">Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="b1c3f-171">Můžete například chtít, aby několik sledovacích záznamů v několika pracovních postupech bylo označeno jako "poštovní server" = = "pošta Server1".</span><span class="sxs-lookup"><span data-stu-id="b1c3f-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="b1c3f-172">To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="b1c3f-173">K tomu je přidána poznámka do sledovacího dotazu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

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

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="b1c3f-174">Postup vytvoření profilu sledování</span><span class="sxs-lookup"><span data-stu-id="b1c3f-174">How to Create a Tracking Profile</span></span>

<span data-ttu-id="b1c3f-175">Sledování prvků dotazu slouží k vytvoření profilu sledování pomocí konfiguračního souboru XML nebo kódu [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1c3f-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]code.</span></span> <span data-ttu-id="b1c3f-176">Tady je příklad profilu sledování vytvořeného pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-176">Here is an example of a tracking profile created using a configuration file.</span></span>

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
> <span data-ttu-id="b1c3f-177">V případě WF pomocí hostitele služby pracovního postupu se profil sledování obvykle vytváří pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="b1c3f-178">Je také možné vytvořit profil sledování s kódem pomocí sledovacího profilu a rozhraní API pro sledování dotazů.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="b1c3f-179">Profil nakonfigurovaný jako konfigurační soubor XML je použit pro sledování účastníka pomocí rozšíření chování.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="b1c3f-180">Tento postup je přidán k hostiteli WorkflowServiceHost, jak je popsáno v části Další [Konfigurace sledování pracovního postupu](configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="b1c3f-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="b1c3f-181">Podrobnost sledování záznamů generovaných hostitelem je určena nastavením konfigurace v rámci profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="b1c3f-182">Účastník sledování se přihlašuje k odběru sledování záznamů přidáním dotazů do profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="b1c3f-183">Chcete-li se přihlásit k odběru všech záznamů sledování, je potřeba, abyste profil sledování určili všechny sledovací dotazy pomocí "\*" v polích Název v jednotlivých dotazech.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="b1c3f-184">Tady jsou některé z běžných příkladů sledování profilů.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-184">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="b1c3f-185">Sledovací profil pro získání záznamů a chyb instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-185">A tracking profile to obtain workflow instance records and faults.</span></span>

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

- <span data-ttu-id="b1c3f-186">Profil sledování pro získání všech vlastních záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="b1c3f-186">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="b1c3f-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1c3f-187">See also</span></span>

- [<span data-ttu-id="b1c3f-188">Sledování SQL</span><span class="sxs-lookup"><span data-stu-id="b1c3f-188">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="b1c3f-189">[Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b1c3f-189">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="b1c3f-190">[Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b1c3f-190">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
