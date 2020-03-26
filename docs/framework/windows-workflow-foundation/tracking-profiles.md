---
title: Sledování profilů
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 609c3f0c728e71d1bbf5335aae0b18d6f99a7181
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249035"
---
# <a name="tracking-profiles"></a><span data-ttu-id="84ff4-102">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="84ff4-102">Tracking Profiles</span></span>

<span data-ttu-id="84ff4-103">Profily sledování obsahují sledovací dotazy, které umožňují účastníkovi sledování přihlásit se k odběru událostí pracovního postupu, které jsou emitovány při změně stavu instance pracovního postupu za běhu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-103">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="84ff4-104">Sledování profilů</span><span class="sxs-lookup"><span data-stu-id="84ff4-104">Tracking Profiles</span></span>

<span data-ttu-id="84ff4-105">Profily sledování se používají k určení informací o sledování, které jsou vydávány pro instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-105">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="84ff4-106">Pokud není zadán žádný profil, jsou emitovány všechny události sledování.</span><span class="sxs-lookup"><span data-stu-id="84ff4-106">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="84ff4-107">Pokud je zadán profil, budou emitovány události sledování zadané v profilu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-107">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="84ff4-108">V závislosti na požadavcích na monitorování můžete napsat profil, který je velmi obecný, který se přihlásí k malé sadě změn stavu vysoké úrovně v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-108">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="84ff4-109">Naopak můžete vytvořit velmi podrobný profil, jehož výsledné události jsou dostatečně bohaté na to, aby později rekonstruovaly podrobný tok spuštění.</span><span class="sxs-lookup"><span data-stu-id="84ff4-109">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="84ff4-110">Sledovací profily se projevují jako elementy XML v rámci standardního konfiguračního souboru rozhraní .NET Framework nebo zadaném v kódu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-110">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="84ff4-111">Následující příklad je [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profil sledování v konfiguračním souboru, `Started` `Completed` který umožňuje účastníkovi sledování přihlásit k odběru událostí a pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-111">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

```xml
<system.serviceModel>
    ...
    <tracking>
     <profiles>
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

<span data-ttu-id="84ff4-112">Následující příklad ukazuje ekvivalentní profil sledování vytvořený pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-112">The following example shows the equivalent tracking profile created using code.</span></span>

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

<span data-ttu-id="84ff4-113">Záznamy sledování jsou filtrovány prostřednictvím režimu viditelnosti <xref:System.Activities.Tracking.ImplementationVisibility> v rámci profilu sledování pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-113">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="84ff4-114">Složená aktivita je aktivita nejvyšší úrovně, která obsahuje další aktivity, které tvoří jeho implementaci.</span><span class="sxs-lookup"><span data-stu-id="84ff4-114">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="84ff4-115">Režim viditelnosti určuje sledování záznamů vyzařovaných z složených aktivit v rámci aktivity pracovního postupu, chcete-li určit, zda jsou sledovány aktivity, které tvoří implementaci.</span><span class="sxs-lookup"><span data-stu-id="84ff4-115">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="84ff4-116">Režim viditelnosti platí na úrovni profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="84ff4-116">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="84ff4-117">Filtrování sledování záznamů pro jednotlivé aktivity v rámci pracovního postupu je řízeno dotazy v rámci profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="84ff4-117">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="84ff4-118">Další informace naleznete v části **Typy dotazů profilu sledování** v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-118">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="84ff4-119">Dva režimy viditelnosti `implementationVisibility` určené atributem v `RootScope` `All`profilu sledování jsou a .</span><span class="sxs-lookup"><span data-stu-id="84ff4-119">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="84ff4-120">Použití `RootScope` režimu potlačí záznamy sledování pro aktivity, které tvoří implementaci aktivity v případě, že složená aktivita není kořenem pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-120">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="84ff4-121">To znamená, že při aktivitě, která je implementována `implementationVisibility` pomocí jiných aktivit, je přidána do pracovního postupu a nastavena na RootScope, je sledována pouze aktivita nejvyšší úrovně v rámci této složené aktivity.</span><span class="sxs-lookup"><span data-stu-id="84ff4-121">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="84ff4-122">Pokud je aktivita kořenem pracovního postupu, pak implementace aktivity je samotný pracovní postup a sledování záznamů jsou vydávány pro aktivity, které tvoří implementaci.</span><span class="sxs-lookup"><span data-stu-id="84ff4-122">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="84ff4-123">Použití režimu Vše umožňuje, aby byly emitovány všechny záznamy sledování pro kořenovou aktivitu a všechny její složené aktivity.</span><span class="sxs-lookup"><span data-stu-id="84ff4-123">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="84ff4-124">Předpokládejme například, že *MyActivity* je složená aktivita, jejíž implementace obsahuje dvě aktivity, *Activity1* a *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="84ff4-124">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="84ff4-125">Pokud je tato aktivita přidána do pracovního `implementationVisibility` postupu `RootScope`a sledování je povoleno s profilem sledování s nastavenou na , jsou záznamy sledování emitovány pouze pro *MyActivity*.</span><span class="sxs-lookup"><span data-stu-id="84ff4-125">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="84ff4-126">Nejsou však vyzařovány žádné záznamy pro aktivity *Activity1* a *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="84ff4-126">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="84ff4-127">Pokud je `implementationVisibility` však atribut pro profil `All`sledování nastaven na , jsou záznamy sledování emitovány nejen pro *MyActivity*, ale také pro aktivity *Activity1* a *Activity2*.</span><span class="sxs-lookup"><span data-stu-id="84ff4-127">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="84ff4-128">Příznak `implementationVisibility` se vztahuje na následující typy záznamů sledování:</span><span class="sxs-lookup"><span data-stu-id="84ff4-128">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="84ff4-129">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="84ff4-129">ActivityStateRecord</span></span>

- <span data-ttu-id="84ff4-130">Záznam propagace faultpro</span><span class="sxs-lookup"><span data-stu-id="84ff4-130">FaultPropagationRecord</span></span>

- <span data-ttu-id="84ff4-131">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="84ff4-131">CancelRequestedRecord</span></span>

- <span data-ttu-id="84ff4-132">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="84ff4-132">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="84ff4-133">CustomTrackingRecords vyzařované z implementace aktivity nejsou odfiltrovány implementacíVisibility nastavení.</span><span class="sxs-lookup"><span data-stu-id="84ff4-133">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="84ff4-134">Funkce `implementationVisibility` je určena <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> jako na sledování profilu v kódu takto:</span><span class="sxs-lookup"><span data-stu-id="84ff4-134">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="84ff4-135">Funkce `implementationVisibility` je určena <xref:System.Activities.Tracking.ImplementationVisibility.All> jako na sledování profilu v konfiguračním souboru takto:</span><span class="sxs-lookup"><span data-stu-id="84ff4-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

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

<span data-ttu-id="84ff4-136">Nastavení `ImplementationVisibility` na profilu sledování je volitelné.</span><span class="sxs-lookup"><span data-stu-id="84ff4-136">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="84ff4-137">Ve výchozím nastavení je `RootScope`jeho hodnota nastavena na hodnotu .</span><span class="sxs-lookup"><span data-stu-id="84ff4-137">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="84ff4-138">Hodnoty pro tento atribut jsou také malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="84ff4-138">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="84ff4-139">Sledování typů dotazů profilu</span><span class="sxs-lookup"><span data-stu-id="84ff4-139">Tracking Profile Query Types</span></span>

<span data-ttu-id="84ff4-140">Sledování profily mají strukturu deklarativní odběrů pro sledování záznamů, které umožňují dotazů modulu runtime pracovního postupu pro záznamy sledování.</span><span class="sxs-lookup"><span data-stu-id="84ff4-140">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="84ff4-141">Existuje několik typů dotazů, které umožňují <xref:System.Activities.Tracking.TrackingRecord> přihlásit se k odběru různých tříd objektů.</span><span class="sxs-lookup"><span data-stu-id="84ff4-141">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="84ff4-142">Profily sledování lze zadat v konfiguraci nebo prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-142">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="84ff4-143">Zde jsou nejběžnější typy dotazů:</span><span class="sxs-lookup"><span data-stu-id="84ff4-143">Here are the most common query types:</span></span>

- <span data-ttu-id="84ff4-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery>- Slouží ke sledování změn životního cyklu instance `Started` pracovního postupu, jako jsou dříve demonstrované a `Completed`.</span><span class="sxs-lookup"><span data-stu-id="84ff4-144"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="84ff4-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Se používá k přihlášení k odběru následující <xref:System.Activities.Tracking.TrackingRecord> objekty:</span><span class="sxs-lookup"><span data-stu-id="84ff4-145">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="84ff4-146">Stavy, které lze přihlásit k <xref:System.Activities.Tracking.WorkflowInstanceStates> odběru jsou určeny ve třídě.</span><span class="sxs-lookup"><span data-stu-id="84ff4-146">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="84ff4-147">Konfigurace nebo kód použitý k odběru záznamů sledování `Started` na úrovni <xref:System.Activities.Tracking.WorkflowInstanceQuery> instance pracovního postupu pro stav instance pomocí uvedeného v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-147">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="84ff4-148"><xref:System.Activities.Tracking.ActivityStateQuery>- Slouží ke sledování změn životního cyklu aktivit, které tvoří instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-148"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="84ff4-149">Můžete například sledovat pokaždé, když se aktivita "Odeslat e-mail" dokončí v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-149">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="84ff4-150">Tento dotaz je <xref:System.Activities.Tracking.TrackingParticipant> nezbytné pro <xref:System.Activities.Tracking.ActivityStateRecord> odběr k odběru objektů.</span><span class="sxs-lookup"><span data-stu-id="84ff4-150">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="84ff4-151">Dostupné stavy, k jejichž <xref:System.Activities.Tracking.ActivityStates>odběru se chcete přihlásit, jsou uvedeny v .</span><span class="sxs-lookup"><span data-stu-id="84ff4-151">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="84ff4-152">Konfigurace a kód použitý k odběru záznamů <xref:System.Activities.Tracking.ActivityStateQuery> sledování `SendEmailActivity` stavu aktivity, které používají pro aktivitu, jsou uvedeny v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-152">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

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
  > <span data-ttu-id="84ff4-153">Pokud více activityStateQuery prvky mají stejný název, pouze stavy v poslední prvek se používají v profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="84ff4-153">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="84ff4-154"><xref:System.Activities.Tracking.ActivityScheduledQuery>- Tento dotaz umožňuje sledovat aktivitu naplánovanou k provedení nadřazenou aktivitou.</span><span class="sxs-lookup"><span data-stu-id="84ff4-154"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="84ff4-155">Dotaz je nezbytné <xref:System.Activities.Tracking.TrackingParticipant> pro odběr <xref:System.Activities.Tracking.ActivityScheduledRecord> k odběru objektů.</span><span class="sxs-lookup"><span data-stu-id="84ff4-155">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="84ff4-156">Konfigurace a kód použitý k odběru `SendEmailActivity` záznamů souvisejících s <xref:System.Activities.Tracking.ActivityScheduledQuery> podřízenou aktivitou naplánovanou pomocí následujícího příkladu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-156">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="84ff4-157"><xref:System.Activities.Tracking.FaultPropagationQuery>- Použijte ke sledování zpracování chyb, ke kterým dochází v rámci aktivity.</span><span class="sxs-lookup"><span data-stu-id="84ff4-157"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="84ff4-158">Dotaz je nezbytné <xref:System.Activities.Tracking.TrackingParticipant> pro odběr <xref:System.Activities.Tracking.FaultPropagationRecord> k odběru objektů.</span><span class="sxs-lookup"><span data-stu-id="84ff4-158">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="84ff4-159">Konfigurace a kód použitý k odběru záznamů souvisejících <xref:System.Activities.Tracking.FaultPropagationQuery> s šířením chyb pomocí je uveden v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-159">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="84ff4-160"><xref:System.Activities.Tracking.CancelRequestedQuery>- Slouží ke sledování požadavků na zrušení podřízené aktivity nadřazenou aktivitou.</span><span class="sxs-lookup"><span data-stu-id="84ff4-160"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="84ff4-161">Dotaz je nezbytné <xref:System.Activities.Tracking.TrackingParticipant> pro odběr <xref:System.Activities.Tracking.CancelRequestedRecord> k odběru objektů.</span><span class="sxs-lookup"><span data-stu-id="84ff4-161">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="84ff4-162">Konfigurace a kód použitý k odběru záznamů <xref:System.Activities.Tracking.CancelRequestedQuery> souvisejících se zrušením aktivity pomocí je uveden v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-162">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="84ff4-163"><xref:System.Activities.Tracking.CustomTrackingQuery>- Pomocí tohoto můžete sledovat události, které definujete v kódu aktivity.</span><span class="sxs-lookup"><span data-stu-id="84ff4-163"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="84ff4-164">Dotaz je nezbytné <xref:System.Activities.Tracking.TrackingParticipant> pro odběr <xref:System.Activities.Tracking.CustomTrackingRecord> k odběru objektů.</span><span class="sxs-lookup"><span data-stu-id="84ff4-164">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="84ff4-165">Konfigurace a kód použitý k přihlášení k odběru <xref:System.Activities.Tracking.CustomTrackingQuery> záznamů souvisejících s vlastními záznamy sledování pomocí je uveden v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-165">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

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

- <span data-ttu-id="84ff4-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery>- Pomocí tohoto můžete sledovat obnovení záložky v rámci instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-166"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="84ff4-167">Tento dotaz je <xref:System.Activities.Tracking.TrackingParticipant> nezbytné pro <xref:System.Activities.Tracking.BookmarkResumptionRecord> odběr k odběru objektů.</span><span class="sxs-lookup"><span data-stu-id="84ff4-167">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="84ff4-168">Konfigurace a kód použitý k odběru záznamů souvisejících s obnovením záložky pomocí <xref:System.Activities.Tracking.BookmarkResumptionQuery> je uveden v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-168">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

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

### <a name="annotations"></a><span data-ttu-id="84ff4-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84ff4-169">Annotations</span></span>

<span data-ttu-id="84ff4-170">Anotace umožňují libovolně značku sledování záznamů s hodnotou, kterou lze nakonfigurovat po čas sestavení.</span><span class="sxs-lookup"><span data-stu-id="84ff4-170">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="84ff4-171">Můžete například chtít, aby bylo několik záznamů sledování v několika pracovních postupech označeno "Poštovním serverem" == "Poštovní server1".</span><span class="sxs-lookup"><span data-stu-id="84ff4-171">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="84ff4-172">To umožňuje snadno vyhledat všechny záznamy s touto značkou při dotazování sledování záznamy později.</span><span class="sxs-lookup"><span data-stu-id="84ff4-172">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="84ff4-173">Chcete-li to provést, je do sledovacího dotazu přidána anotace, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-173">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

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

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="84ff4-174">Jak vytvořit profil sledování</span><span class="sxs-lookup"><span data-stu-id="84ff4-174">How to Create a Tracking Profile</span></span>

<span data-ttu-id="84ff4-175">Prvky sledovacího dotazu se používají k vytvoření [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] profilu sledování pomocí konfiguračního souboru XML nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="84ff4-175">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] code.</span></span> <span data-ttu-id="84ff4-176">Zde je příklad profilu sledování vytvořeného pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="84ff4-176">Here is an example of a tracking profile created using a configuration file.</span></span>

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
> <span data-ttu-id="84ff4-177">Pro wf pomocí hostitele služby Workflow je profil sledování obvykle vytvořen pomocí konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="84ff4-177">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="84ff4-178">Je také možné vytvořit profil sledování s kódem pomocí sledování profilu a sledování dotazu ROZHRANÍ API.</span><span class="sxs-lookup"><span data-stu-id="84ff4-178">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="84ff4-179">Profil nakonfigurovaný jako konfigurační soubor XML se použije na účastníka sledování pomocí přípony chování.</span><span class="sxs-lookup"><span data-stu-id="84ff4-179">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="84ff4-180">To je přidáno do WorkflowServiceHost, jak je popsáno v další části [Konfigurace sledování pro pracovní postup](configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="84ff4-180">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="84ff4-181">Podrobnost záznamů sledování vyzařovaných hostitelem je určena nastavením konfigurace v rámci profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="84ff4-181">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="84ff4-182">Účastník sledování se přihlásí ke sledování záznamů přidáním dotazů do profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="84ff4-182">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="84ff4-183">Chcete-li se přihlásit k odběru všech záznamů sledování,\*musí profil sledování zadat všechny sledovací dotazy pomocí " " v polích názvů v každém z dotazů.</span><span class="sxs-lookup"><span data-stu-id="84ff4-183">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="84ff4-184">Zde jsou některé z běžných příkladů sledování profilů.</span><span class="sxs-lookup"><span data-stu-id="84ff4-184">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="84ff4-185">Profil sledování pro získání záznamů instancí pracovního postupu a chyb.</span><span class="sxs-lookup"><span data-stu-id="84ff4-185">A tracking profile to obtain workflow instance records and faults.</span></span>

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

- <span data-ttu-id="84ff4-186">Profil sledování pro získání všech vlastních záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="84ff4-186">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="84ff4-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="84ff4-187">See also</span></span>

- [<span data-ttu-id="84ff4-188">Sledování SQL</span><span class="sxs-lookup"><span data-stu-id="84ff4-188">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="84ff4-189">[Monitorování prostředků infrastruktury aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="84ff4-189">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="84ff4-190">[Monitorování aplikací pomocí prostředků infrastruktury aplikací](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="84ff4-190">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
