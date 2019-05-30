---
title: Použití WorkflowIdentity a správy verzí
ms.date: 03/30/2017
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
ms.openlocfilehash: acf2b2c9502487c8bc8960f2a5625db94c31945f
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380122"
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="e33ee-102">Použití WorkflowIdentity a správy verzí</span><span class="sxs-lookup"><span data-stu-id="e33ee-102">Using WorkflowIdentity and Versioning</span></span>
<span data-ttu-id="e33ee-103"><xref:System.Activities.WorkflowIdentity> nabízí způsob, jak pro pracovní postup přidružit název a <xref:System.Version> s definicí pracovního postupu a tyto informace k trvalé instance práce.</span><span class="sxs-lookup"><span data-stu-id="e33ee-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="e33ee-104">Tyto informace identita umožňuje vývojáři aplikace pracovního postupu povolení scénářů, jako je vedle sebe spuštění více verzí modulu definice pracovního postupu a poskytuje základní kámen pro další funkce, jako je například dynamická aktualizace.</span><span class="sxs-lookup"><span data-stu-id="e33ee-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="e33ee-105">Toto téma obsahuje přehled používání <xref:System.Activities.WorkflowIdentity> s <xref:System.Activities.WorkflowApplication> hostování.</span><span class="sxs-lookup"><span data-stu-id="e33ee-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="e33ee-106">Informace o spuštění vedle sebe definice pracovního postupu ve službě pracovního postupu v tématu [správy verzí vedle sebe ve třídě WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="e33ee-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="e33ee-107">Informace o dynamické aktualizace, naleznete v tématu [dynamická aktualizace](dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="e33ee-107">For information on dynamic update, see [Dynamic Update](dynamic-update.md).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="e33ee-108">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="e33ee-108">In this topic</span></span>  
  
- [<span data-ttu-id="e33ee-109">Pomocí identita WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="e33ee-109">Using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    - [<span data-ttu-id="e33ee-110">Pomocí identita WorkflowIdentity spuštění vedle sebe</span><span class="sxs-lookup"><span data-stu-id="e33ee-110">Side-by-side Execution using WorkflowIdentity</span></span>](using-workflowidentity-and-versioning.md#SxS)  
  
- [<span data-ttu-id="e33ee-111">Upgrade rozhraní .NET Framework 4 trvalost databází pro podporu správy verzí pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e33ee-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    - [<span data-ttu-id="e33ee-112">Aktualizace schématu databáze</span><span class="sxs-lookup"><span data-stu-id="e33ee-112">To upgrade the database schema</span></span>](using-workflowidentity-and-versioning.md#ToUpgrade)  
  
## <a name="UsingWorkflowIdentity"></a> <span data-ttu-id="e33ee-113">Pomocí identita WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="e33ee-113">Using WorkflowIdentity</span></span>  
 <span data-ttu-id="e33ee-114">Použití <xref:System.Activities.WorkflowIdentity>vytvořit instanci, nakonfigurujte ji a přidružte jej k <xref:System.Activities.WorkflowApplication> instance.</span><span class="sxs-lookup"><span data-stu-id="e33ee-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="e33ee-115">A <xref:System.Activities.WorkflowIdentity> instance obsahuje tři identifikační údaje.</span><span class="sxs-lookup"><span data-stu-id="e33ee-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="e33ee-116"><xref:System.Activities.WorkflowIdentity.Name%2A> a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahovat název a <xref:System.Version> a jsou povinné, a <xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a slouží k určení další řetězec obsahující informace, jako je název sestavení nebo jiné požadované informace.</span><span class="sxs-lookup"><span data-stu-id="e33ee-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="e33ee-117">A <xref:System.Activities.WorkflowIdentity> je jedinečné, pokud některý z jeho tři vlastnosti se liší od jiného <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="e33ee-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e33ee-118">A <xref:System.Activities.WorkflowIdentity> nesmí obsahovat žádné identifikovatelné osobní údaje (PII).</span><span class="sxs-lookup"><span data-stu-id="e33ee-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="e33ee-119">Informace o <xref:System.Activities.WorkflowIdentity> použitý k vytvoření instance je vygenerován pro všechny nakonfigurované sledování životního cyklu služeb v několika různých fázích aktivity modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="e33ee-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="e33ee-120">Sledování WF nemá žádný mechanismus skrýt identifikovatelné osobní údaje (citlivými daty).</span><span class="sxs-lookup"><span data-stu-id="e33ee-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="e33ee-121">Proto <xref:System.Activities.WorkflowIdentity> instance by neměla obsahovat žádná data identifikovatelné osobní údaje, jak bude vygenerován modulem runtime ve sledování záznamů a mohou být viditelná pro každý, kdo má přístup k zobrazení záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="e33ee-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
 <span data-ttu-id="e33ee-122">V následujícím příkladu <xref:System.Activities.WorkflowIdentity> se vytvoří a přidružené k instanci pracovního postupu vytvořené využitím `MortgageWorkflow` definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e33ee-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>  
  
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
  
 <span data-ttu-id="e33ee-123">Při opětovném načtení a obnovení pracovního postupu, <xref:System.Activities.WorkflowIdentity> , který je nakonfigurovaný tak, aby odpovídaly <xref:System.Activities.WorkflowIdentity> trvalá pracovního postupu instance musí být použita.</span><span class="sxs-lookup"><span data-stu-id="e33ee-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="e33ee-124">Pokud <xref:System.Activities.WorkflowIdentity> při opětovném načtení instance pracovního postupu se neshoduje trvalý <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e33ee-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="e33ee-125">V následujícím příkladu pokusu o načtení se provádí na `MortgageWorkflow` instanci, která byla zachována v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e33ee-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="e33ee-126">Tato zatížení pokus se uskuteční pomocí <xref:System.Activities.WorkflowIdentity> nakonfigurovaný pro novější verze na dům pracovního postupu, který se neshoduje s trvalé instanci.</span><span class="sxs-lookup"><span data-stu-id="e33ee-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="e33ee-127">Když je spuštěn předchozí kód, následující <xref:System.Activities.VersionMismatchException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e33ee-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>  
  
 <span data-ttu-id="e33ee-128">**Identita WorkflowIdentity ("MortgageWorkflow v1; Verze = 1.0.0.0') načtené instance neodpovídá identitě WorkflowIdentity ("MortgageWorkflow v2; Verze = 2.0.0.0') definice pracovního postupu. Tuto instanci lze načíst s použitím jiné definice nebo ji aktualizovat pomocí dynamické aktualizace.**</span><span class="sxs-lookup"><span data-stu-id="e33ee-128">**The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.**</span></span>  
### <a name="SxS"></a> <span data-ttu-id="e33ee-129">Pomocí identita WorkflowIdentity spuštění vedle sebe</span><span class="sxs-lookup"><span data-stu-id="e33ee-129">Side-by-side Execution using WorkflowIdentity</span></span>  
 <span data-ttu-id="e33ee-130"><xref:System.Activities.WorkflowIdentity> slouží k usnadnění spuštění více verzí pracovní postup-souběžně.</span><span class="sxs-lookup"><span data-stu-id="e33ee-130"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="e33ee-131">Jeden běžný scénář se mění obchodní požadavky v rámci dlouhotrvající pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e33ee-131">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="e33ee-132">Velký počet instancí pracovního postupu může být spuštěn při nasazení aktualizované verze.</span><span class="sxs-lookup"><span data-stu-id="e33ee-132">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="e33ee-133">Hostitelská aplikace je nakonfigurovat pro použití definice aktualizovaný pracovní postup při spuštění nové instance a zodpovídá hostitelskou aplikaci poskytnout definici správné pracovního postupu při opětovném spuštění instance.</span><span class="sxs-lookup"><span data-stu-id="e33ee-133">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="e33ee-134"><xref:System.Activities.WorkflowIdentity> je možné identifikovat a zadat odpovídající definice pracovního postupu při opětovném spuštění instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e33ee-134"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>  
  
 <span data-ttu-id="e33ee-135">Načíst <xref:System.Activities.WorkflowIdentity> z trvalé instance práce, <xref:System.Activities.WorkflowApplication.GetInstance%2A> metoda se používá.</span><span class="sxs-lookup"><span data-stu-id="e33ee-135">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="e33ee-136"><xref:System.Activities.WorkflowApplication.GetInstance%2A> Přijímá metodu <xref:System.Activities.WorkflowApplication.Id%2A> instance trvalá pracovního postupu a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , který obsahuje trvalé instanci a vrátí <xref:System.Activities.WorkflowApplicationInstance>.</span><span class="sxs-lookup"><span data-stu-id="e33ee-136">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="e33ee-137">A <xref:System.Activities.WorkflowApplicationInstance> obsahuje informace o trvalé instance práce, včetně jeho přidruženého <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="e33ee-137">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="e33ee-138">Tato související <xref:System.Activities.WorkflowIdentity> je možné zadat definici správné pracovního postupu při načítání a obnovení instance pracovního postupu hostitele.</span><span class="sxs-lookup"><span data-stu-id="e33ee-138">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e33ee-139">S hodnotou null <xref:System.Activities.WorkflowIdentity> je platný a je možné mapovat instancí, které byly trvale uložena s žádné přidružené hostitelem <xref:System.Activities.WorkflowIdentity> k definici pracovního postupu správné.</span><span class="sxs-lookup"><span data-stu-id="e33ee-139">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="e33ee-140">Tato situace může nastat, když aplikace pracovního postupu nebyl původně zapsán s verzí pracovního postupu, nebo když aplikace se upgraduje z [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e33ee-140">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="e33ee-141">Další informace najdete v tématu [upgrade rozhraní .NET Framework 4 trvalost databází na podporu pracovních postupů správy verzí](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="e33ee-141">For more information, see [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>  
  
 <span data-ttu-id="e33ee-142">V následujícím příkladu `Dictionary<WorkflowIdentity, Activity>` slouží k přidružení <xref:System.Activities.WorkflowIdentity> instance s jejich odpovídající definice pracovního postupu a pracovní postup je začít používat `MortgageWorkflow` definice pracovního postupu, který je přidružený `identityV1` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="e33ee-142">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
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
  
 <span data-ttu-id="e33ee-143">V následujícím příkladu je načíst informace o instanci trvalá pracovního postupu z předchozího příkladu voláním <xref:System.Activities.WorkflowApplication.GetInstance%2A>a trvalý <xref:System.Activities.WorkflowIdentity> informace slouží k načtení odpovídajícího definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e33ee-143">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="e33ee-144">Tyto informace slouží ke konfiguraci <xref:System.Activities.WorkflowApplication>, a pak je načíst pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="e33ee-144">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="e33ee-145">Upozorňujeme, že <xref:System.Activities.WorkflowApplication.Load%2A> přetížení přebírající <xref:System.Activities.WorkflowApplicationInstance> se používá, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> , který byl nakonfigurován na <xref:System.Activities.WorkflowApplicationInstance> používá <xref:System.Activities.WorkflowApplication> a proto jeho <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost není nutné konfigurovat.</span><span class="sxs-lookup"><span data-stu-id="e33ee-145">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e33ee-146">Pokud <xref:System.Activities.WorkflowApplication.InstanceStore%2A> je hodnota nastavena, je nutné ji nastavit pomocí stejné <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instanci použitou <xref:System.Activities.WorkflowApplicationInstance> jinak <xref:System.ArgumentException> bude vyvolána výjimka s následující zprávou: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span><span class="sxs-lookup"><span data-stu-id="e33ee-146">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>  
  
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
  
## <a name="UpdatingWF4PersistenceDatabases"></a> <span data-ttu-id="e33ee-147">Upgrade rozhraní .NET Framework 4 trvalost databází pro podporu správy verzí pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e33ee-147">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>  
 <span data-ttu-id="e33ee-148">Upgrade databáze trvalosti vytvořené ve službě je poskytován skript databáze SqlWorkflowInstanceStoreSchemaUpgrade.sql [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] databázové skripty.</span><span class="sxs-lookup"><span data-stu-id="e33ee-148">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] database scripts.</span></span> <span data-ttu-id="e33ee-149">Tento skript aktualizace databází, aby podporovaly nové funkce správy verzí zavedena v rozhraní .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="e33ee-149">This script updates the databases to support the new versioning capabilities introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="e33ee-150">Všechny instance trvalá pracovního postupu v databázích jsou uvedeny výchozí hodnoty správy verzí a potom účastnit spuštění vedle sebe a dynamické aktualizace.</span><span class="sxs-lookup"><span data-stu-id="e33ee-150">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>  
  
 <span data-ttu-id="e33ee-151">Pokud se aplikace pracovního postupu rozhraní .NET Framework 4.5 pokusí všechny operace trvalého uložení, které používají nové funkce správy verzí na stálost databázi, která nebyla upgradována pomocí dodávaného skriptu <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> dojde a zobrazí se zpráva podobná následující zpráva.</span><span class="sxs-lookup"><span data-stu-id="e33ee-151">If a .NET Framework 4.5 workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>  
  
 <span data-ttu-id="e33ee-152">**Úložiště SqlWorkflowInstanceStore je verze databáze "4.0.0.0". Příkaz InstancePersistenceCommand "System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand" nelze spustit proti této verzi databáze.  Upgradujte databázi na "4.5.0.0".**</span><span class="sxs-lookup"><span data-stu-id="e33ee-152">**The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.**</span></span>  
### <a name="ToUpgrade"></a> <span data-ttu-id="e33ee-153">Aktualizace schématu databáze</span><span class="sxs-lookup"><span data-stu-id="e33ee-153">To upgrade the database schema</span></span>  
  
1. <span data-ttu-id="e33ee-154">Otevřete SQL Server Management Studio a připojte se k serveru databáze trvalosti, například **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="e33ee-154">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>  
  
2. <span data-ttu-id="e33ee-155">Zvolte **otevřít**, **souboru** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e33ee-155">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="e33ee-156">Přejděte do následující složky: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="e33ee-156">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span></span>  
  
3. <span data-ttu-id="e33ee-157">Vyberte **SqlWorkflowInstanceStoreSchemaUpgrade.sql** a klikněte na tlačítko **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="e33ee-157">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>  
  
4. <span data-ttu-id="e33ee-158">Vyberte název databáze trvalosti v **dostupných databází** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="e33ee-158">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>  
  
5. <span data-ttu-id="e33ee-159">Zvolte **Execute** z **dotazu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="e33ee-159">Choose **Execute** from the **Query** menu.</span></span>  
  
 <span data-ttu-id="e33ee-160">Po dokončení dotazu schéma databáze se upgraduje a v případě potřeby můžete zobrazit výchozí identity pracovního postupu, která byla přiřazena instance trvalá pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e33ee-160">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="e33ee-161">Rozbalte databázi přetrvávání v **databází** uzlu **Průzkumník objektů**a potom rozbalte **zobrazení** uzlu.</span><span class="sxs-lookup"><span data-stu-id="e33ee-161">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="e33ee-162">Klikněte pravým tlačítkem na **System.Activities.DurableInstancing.Instances** a zvolte **vybrat prvních 1000 řádků**.</span><span class="sxs-lookup"><span data-stu-id="e33ee-162">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="e33ee-163">Přejděte na konec sloupců a Všimněte si, že jsou šest další sloupce, které jsou přidány do zobrazení: **IdentityName**, **IdentityPackage**, **sestavení**, **hlavní**, **menší**, a **revize**.</span><span class="sxs-lookup"><span data-stu-id="e33ee-163">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="e33ee-164">Žádný trvalý pracovní postup bude mít hodnotu **NULL** tato pole představující identity pracovního postupu hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e33ee-164">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
