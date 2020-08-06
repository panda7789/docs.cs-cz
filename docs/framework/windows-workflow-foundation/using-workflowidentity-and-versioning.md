---
title: Použití WorkflowIdentity a správy verzí
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: 1d31739c135dbb518f05c40ba802c782b6817bff
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855631"
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="abd52-102">Použití WorkflowIdentity a správy verzí</span><span class="sxs-lookup"><span data-stu-id="abd52-102">Using WorkflowIdentity and Versioning</span></span>

<span data-ttu-id="abd52-103"><xref:System.Activities.WorkflowIdentity>poskytuje způsob, jak můžou vývojáři aplikací pracovních postupů přidružit název a <xref:System.Version> definici pracovního postupu a pro tyto informace musí být přidružené k trvalé instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="abd52-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="abd52-104">Tyto informace o identitě mohou vývojáři aplikací pracovních postupů použít k povolení scénářů, jako je souběžné spouštění více verzí definice pracovního postupu, a poskytuje základní kámen pro jiné funkce, jako je například dynamická aktualizace.</span><span class="sxs-lookup"><span data-stu-id="abd52-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="abd52-105">Toto téma poskytuje přehled o použití <xref:System.Activities.WorkflowIdentity> s <xref:System.Activities.WorkflowApplication> hostováním.</span><span class="sxs-lookup"><span data-stu-id="abd52-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="abd52-106">Informace o souběžném spouštění definic pracovních postupů ve službě pracovního postupu najdete v tématu [Správa verzí vedle sebe v hostiteli WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="abd52-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="abd52-107">Informace o dynamické aktualizaci najdete v tématu [Dynamická aktualizace](dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="abd52-107">For information on dynamic update, see [Dynamic Update](dynamic-update.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="abd52-108">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="abd52-108">In this topic</span></span>

- [<span data-ttu-id="abd52-109">Použití identita WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="abd52-109">Using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)

  - [<span data-ttu-id="abd52-110">Souběžné spouštění pomocí identita WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="abd52-110">Side-by-side Execution using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#SxS)

- [<span data-ttu-id="abd52-111">Upgrade databází trvalosti .NET Framework 4 pro podporu správy verzí pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="abd52-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)

  - [<span data-ttu-id="abd52-112">Postup upgradu schématu databáze</span><span class="sxs-lookup"><span data-stu-id="abd52-112">To upgrade the database schema</span></span>](using-workflowidentity-and-versioning.md#ToUpgrade)

## <a name="using-workflowidentity"></a><a name="UsingWorkflowIdentity"></a><span data-ttu-id="abd52-113">Použití identita WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="abd52-113">Using WorkflowIdentity</span></span>

<span data-ttu-id="abd52-114">Chcete-li použít <xref:System.Activities.WorkflowIdentity> , vytvořte instanci, nakonfigurujte ji a přidružte ji k <xref:System.Activities.WorkflowApplication> instanci.</span><span class="sxs-lookup"><span data-stu-id="abd52-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="abd52-115"><xref:System.Activities.WorkflowIdentity>Instance obsahuje tři identifikační části informací.</span><span class="sxs-lookup"><span data-stu-id="abd52-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="abd52-116"><xref:System.Activities.WorkflowIdentity.Name%2A>a <xref:System.Activities.WorkflowIdentity.Version%2A> musí obsahovat název a <xref:System.Version> a a a <xref:System.Activities.WorkflowIdentity.Package%2A> je nepovinné a lze jej použít k určení dalšího řetězce obsahujícího informace, jako je například název sestavení nebo jiné požadované informace.</span><span class="sxs-lookup"><span data-stu-id="abd52-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="abd52-117">Objekt <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud se některá z jeho tří vlastností liší od jiného <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="abd52-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abd52-118"><xref:System.Activities.WorkflowIdentity>By neměl obsahovat žádné identifikovatelné osobní údaje (PII).</span><span class="sxs-lookup"><span data-stu-id="abd52-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="abd52-119">Informace o <xref:System.Activities.WorkflowIdentity> použití pro vytvoření instance jsou generovány do všech nakonfigurovaných služeb sledování v několika různých místech životního cyklu aktivity modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="abd52-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="abd52-120">Sledování WF nemá žádný mechanismus pro skrytí PII (citlivých uživatelských dat).</span><span class="sxs-lookup"><span data-stu-id="abd52-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="abd52-121"><xref:System.Activities.WorkflowIdentity>Instance by proto neměla obsahovat žádná data PII, protože bude vygenerována modulem runtime ve sledování záznamů a může být viditelná pro kohokoli s přístupem k zobrazení záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="abd52-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>

<span data-ttu-id="abd52-122">V následujícím příkladu <xref:System.Activities.WorkflowIdentity> je vytvořen a přidružen k instanci pracovního postupu vytvořeného pomocí `MortgageWorkflow` definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="abd52-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

<span data-ttu-id="abd52-123">Po opětovném načtení a obnovení pracovního postupu, <xref:System.Activities.WorkflowIdentity> který je nakonfigurován tak, aby odpovídal <xref:System.Activities.WorkflowIdentity> instanci trvalého pracovního postupu, je nutné použít.</span><span class="sxs-lookup"><span data-stu-id="abd52-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the workflow.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="abd52-124">Pokud se <xref:System.Activities.WorkflowIdentity> použití při opětovném načtení instance pracovního postupu neshoduje s trvalým <xref:System.Activities.WorkflowIdentity> , <xref:System.Activities.VersionMismatchException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="abd52-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="abd52-125">V následujícím příkladu je proveden pokus o načtení u `MortgageWorkflow` instance, která byla trvala v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="abd52-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="abd52-126">Tento pokus o načtení se provádí pomocí <xref:System.Activities.WorkflowIdentity> nakonfigurovaného pro novější verzi pracovního postupu hypotéky, která neodpovídá trvalé instanci.</span><span class="sxs-lookup"><span data-stu-id="abd52-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>

```csharp
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Attempt to load the workflow instance.
wfApp.Load(instanceId);

// Resume the workflow...
```

<span data-ttu-id="abd52-127">Po spuštění předchozího kódu <xref:System.Activities.VersionMismatchException> je vyvolána následující výjimka.</span><span class="sxs-lookup"><span data-stu-id="abd52-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>

```output
The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.
```

### <a name="side-by-side-execution-using-workflowidentity"></a><a name="SxS"></a><span data-ttu-id="abd52-128">Souběžné spouštění pomocí identita WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="abd52-128">Side-by-side Execution using WorkflowIdentity</span></span>

<span data-ttu-id="abd52-129"><xref:System.Activities.WorkflowIdentity>dá se použít k usnadnění provádění několika verzí pracovního postupu vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="abd52-129"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="abd52-130">Jedním z běžných scénářů je změna obchodních požadavků na dlouhodobě běžící pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="abd52-130">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="abd52-131">V případě, že je nasazena aktualizovaná verze, může být spuštěno mnoho instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="abd52-131">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="abd52-132">Hostitelská aplikace se dá nakonfigurovat tak, aby při spuštění nových instancí používala aktualizovanou definici pracovního postupu, a je zodpovědností, že hostitelská aplikace poskytne správnou definici pracovního postupu při obnovení instancí.</span><span class="sxs-lookup"><span data-stu-id="abd52-132">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="abd52-133"><xref:System.Activities.WorkflowIdentity>dá se použít k identifikaci a dodávání odpovídajícího definice pracovního postupu při obnovování instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="abd52-133"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>

<span data-ttu-id="abd52-134">Pro načtení <xref:System.Activities.WorkflowIdentity> trvalé instance pracovního postupu <xref:System.Activities.WorkflowApplication.GetInstance%2A> je použita metoda.</span><span class="sxs-lookup"><span data-stu-id="abd52-134">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="abd52-135"><xref:System.Activities.WorkflowApplication.GetInstance%2A>Metoda převezme <xref:System.Activities.WorkflowApplication.Id%2A> instanci trvalého pracovního postupu a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , která obsahuje trvalou instanci a vrátí <xref:System.Activities.WorkflowApplicationInstance> .</span><span class="sxs-lookup"><span data-stu-id="abd52-135">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="abd52-136"><xref:System.Activities.WorkflowApplicationInstance>Obsahuje informace o trvalé instanci pracovního postupu, včetně jejího přidruženého <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="abd52-136">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="abd52-137">Tuto přidruženou adresu <xref:System.Activities.WorkflowIdentity> může hostitel použít k poskytnutí správné definice pracovního postupu při načítání a obnovování instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="abd52-137">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>

> [!NOTE]
> <span data-ttu-id="abd52-138">Hodnota null <xref:System.Activities.WorkflowIdentity> je platná a může být použita hostitelem k mapování instancí, které byly trvale nastaveny bez přidružení <xref:System.Activities.WorkflowIdentity> ke správné definici pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="abd52-138">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="abd52-139">K tomuto scénáři může dojít, když aplikace pracovního postupu nebyla původně zapsána pomocí správy verzí pracovních postupů nebo při upgradu aplikace z .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="abd52-139">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from .NET Framework 4.</span></span> <span data-ttu-id="abd52-140">Další informace najdete v tématu [upgrade databáze .NET Framework 4 Persistence pro podporu správy verzí pracovních postupů](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="abd52-140">For more information, see [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>

<span data-ttu-id="abd52-141">V následujícím příkladu `Dictionary<WorkflowIdentity, Activity>` se používá k přidružení instancí k <xref:System.Activities.WorkflowIdentity> odpovídajícím definicím pracovního postupu a pracovní postup se spustí pomocí `MortgageWorkflow` definice pracovního postupu, která je přidružena k `identityV1` <xref:System.Activities.WorkflowIdentity> .</span><span class="sxs-lookup"><span data-stu-id="abd52-141">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>

```csharp
WorkflowIdentity identityV1 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1",
    Version = new Version(1, 0, 0, 0)
};

WorkflowIdentity identityV2 = new WorkflowIdentity
{
    Name = "MortgageWorkflow v2",
    Version = new Version(2, 0, 0, 0)
};

Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Run the workflow.
wfApp.Run();
```

<span data-ttu-id="abd52-142">V následujícím příkladu jsou informace o trvalé instanci pracovního postupu z předchozího příkladu načteny voláním <xref:System.Activities.WorkflowApplication.GetInstance%2A> a trvalé <xref:System.Activities.WorkflowIdentity> informace jsou použity k načtení odpovídajícího definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="abd52-142">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="abd52-143">Tyto informace slouží ke konfiguraci <xref:System.Activities.WorkflowApplication> a následnému načtení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="abd52-143">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="abd52-144">Všimněte si, že vzhledem k tomu, že <xref:System.Activities.WorkflowApplication.Load%2A> přetížení, které přijímá, je použito <xref:System.Activities.WorkflowApplicationInstance> , <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> které bylo konfigurováno v rozhraní, <xref:System.Activities.WorkflowApplicationInstance> <xref:System.Activities.WorkflowApplication> a proto jeho <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost není nutné konfigurovat.</span><span class="sxs-lookup"><span data-stu-id="abd52-144">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>

> [!NOTE]
> <span data-ttu-id="abd52-145">Pokud <xref:System.Activities.WorkflowApplication.InstanceStore%2A> je vlastnost nastavena, musí být nastavena se stejnou instancí, jakou <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> používá <xref:System.Activities.WorkflowApplicationInstance> nebo else, <xref:System.ArgumentException> bude vyvolána s následující zprávou: `The instance is configured with a different InstanceStore than this WorkflowApplication.` .</span><span class="sxs-lookup"><span data-stu-id="abd52-145">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>

```csharp
// Get the WorkflowApplicationInstance of the desired workflow from the specified
// SqlWorkflowInstanceStore.
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);

// Use the persisted WorkflowIdentity to retrieve the correct workflow
// definition from the dictionary.
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];

WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);

// Configure the WorkflowApplication with persistence and desired workflow event handlers.
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(instance);

// Resume the workflow...
```

## <a name="upgrading-net-framework-4-persistence-databases-to-support-workflow-versioning"></a><a name="UpdatingWF4PersistenceDatabases"></a><span data-ttu-id="abd52-146">Upgrade databází trvalosti .NET Framework 4 pro podporu správy verzí pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="abd52-146">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>

<span data-ttu-id="abd52-147">K upgradu databáze trvalosti vytvořené pomocí databázových skriptů .NET Framework 4 se poskytuje skript databáze SqlWorkflowInstanceStoreSchemaUpgrade. SQL.</span><span class="sxs-lookup"><span data-stu-id="abd52-147">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the .NET Framework 4 database scripts.</span></span> <span data-ttu-id="abd52-148">Tento skript aktualizuje databáze nástroje tak, aby podporovaly nové možnosti správy verzí, zavedené v .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="abd52-148">This script updates the databases to support the new versioning capabilities introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="abd52-149">Všechny trvalé instance pracovního postupu v databázích mají výchozí hodnoty pro správu verzí a můžou se pak zúčastnit souběžného spouštění a dynamické aktualizace.</span><span class="sxs-lookup"><span data-stu-id="abd52-149">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>

<span data-ttu-id="abd52-150">Pokusí-li se aplikace pracovního postupu .NET Framework 4,5 nějaké operace trvalého uložení, které používají nové funkce správy verzí na trvalé databázi, která nebyla upgradována pomocí zadaného skriptu, <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> je vyvolána zpráva podobná následující zprávě.</span><span class="sxs-lookup"><span data-stu-id="abd52-150">If a .NET Framework 4.5 workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>

```output
The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.
```

### <a name="to-upgrade-the-database-schema"></a><a name="ToUpgrade"></a><span data-ttu-id="abd52-151">Postup upgradu schématu databáze</span><span class="sxs-lookup"><span data-stu-id="abd52-151">To upgrade the database schema</span></span>

1. <span data-ttu-id="abd52-152">Otevřete SQL Server Management Studio a připojte se k serveru databáze trvalosti, například **.\SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="abd52-152">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>

2. <span data-ttu-id="abd52-153">V nabídce **soubor** vyberte **otevřít**, **soubor** .</span><span class="sxs-lookup"><span data-stu-id="abd52-153">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="abd52-154">Přejděte do následující složky:`C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="abd52-154">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\v4.0.30319\sql\en`</span></span>

3. <span data-ttu-id="abd52-155">Vyberte **SqlWorkflowInstanceStoreSchemaUpgrade. SQL** a klikněte na **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="abd52-155">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>

4. <span data-ttu-id="abd52-156">V rozevíracím seznamu **dostupné databáze** vyberte název databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="abd52-156">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>

5. <span data-ttu-id="abd52-157">V nabídce **dotaz** klikněte na příkaz **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="abd52-157">Choose **Execute** from the **Query** menu.</span></span>

<span data-ttu-id="abd52-158">Po dokončení dotazu se aktualizuje schéma databáze a v případě potřeby můžete zobrazit výchozí identitu pracovního postupu, která byla přiřazena k trvale vytvořeným instancím pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="abd52-158">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="abd52-159">Rozbalte databázi Persistence v uzlu **databáze** **Průzkumník objektů**a poté rozbalte uzel **zobrazení** .</span><span class="sxs-lookup"><span data-stu-id="abd52-159">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="abd52-160">Klikněte pravým tlačítkem na **System. Activities. DurableInstancing. Instances** a zvolte **Vybrat prvních 1000 řádků**.</span><span class="sxs-lookup"><span data-stu-id="abd52-160">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="abd52-161">Posuňte se na konec sloupců a Všimněte si, že do zobrazení bylo přidáno šest dalších sloupců: **identity**, **IdentityPackage**, **Build**, **hlavní_verze**, **podverze**a **Revize**.</span><span class="sxs-lookup"><span data-stu-id="abd52-161">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="abd52-162">Všechny trvalé pracovní postupy budou mít pro tato pole hodnotu **null** , která představuje identitu pracovního postupu s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="abd52-162">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
