---
title: "Pomocí WorkflowIdentity a správa verzí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02620abf421256b53fb5919b39f441f7346a2e7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="8dd1d-102">Pomocí WorkflowIdentity a správa verzí</span><span class="sxs-lookup"><span data-stu-id="8dd1d-102">Using WorkflowIdentity and Versioning</span></span>
<span data-ttu-id="8dd1d-103"><xref:System.Activities.WorkflowIdentity>poskytuje způsob pro pracovní postup vývojáři aplikace k přidružit název a <xref:System.Version> s definicí pracovního postupu a pro tyto informace k být přidružen k instanci pracovního postupu trvalý.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="8dd1d-104">Tyto informace identity lze použít vývojáři aplikace pracovního postupu povolit scénáře, jako je vedle sebe spouštění více verzí definice pracovního postupu a poskytuje základním kamenem pro další funkce, jako je například dynamická aktualizace.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="8dd1d-105">Toto téma poskytuje přehled používání <xref:System.Activities.WorkflowIdentity> s <xref:System.Activities.WorkflowApplication> hostování.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="8dd1d-106">Informace o provádění vedle sebe definice pracovního postupu v služby pracovního postupu v tématu [správu verzí vedle sebe v hostitele služby pracovního postupu](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="8dd1d-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="8dd1d-107">Informace o dynamické aktualizace, najdete v části [dynamické aktualizace](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="8dd1d-107">For information on dynamic update, see [Dynamic Update](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="8dd1d-108">V tomto tématu</span><span class="sxs-lookup"><span data-stu-id="8dd1d-108">In this topic</span></span>  
  
-   [<span data-ttu-id="8dd1d-109">Pomocí WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="8dd1d-109">Using WorkflowIdentity</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [<span data-ttu-id="8dd1d-110">Pomocí WorkflowIdentity spuštění vedle sebe</span><span class="sxs-lookup"><span data-stu-id="8dd1d-110">Side-by-side Execution using WorkflowIdentity</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [<span data-ttu-id="8dd1d-111">Upgrade rozhraní .NET Framework 4 trvalost databáze podporující pracovní postup správy verzí</span><span class="sxs-lookup"><span data-stu-id="8dd1d-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [<span data-ttu-id="8dd1d-112">Aktualizace schématu databáze</span><span class="sxs-lookup"><span data-stu-id="8dd1d-112">To upgrade the database schema</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
##  <a name="UsingWorkflowIdentity"></a><span data-ttu-id="8dd1d-113">Pomocí WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="8dd1d-113">Using WorkflowIdentity</span></span>  
 <span data-ttu-id="8dd1d-114">Chcete-li použít <xref:System.Activities.WorkflowIdentity>, vytvoření instance, konfiguraci a přidružte ji s <xref:System.Activities.WorkflowApplication> instance.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="8dd1d-115">A <xref:System.Activities.WorkflowIdentity> instance obsahuje tři identifikační údaje.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="8dd1d-116"><xref:System.Activities.WorkflowIdentity.Name%2A>a <xref:System.Activities.WorkflowIdentity.Version%2A> obsahovat název a <xref:System.Version> a jsou povinné, a <xref:System.Activities.WorkflowIdentity.Package%2A> je volitelný a může sloužit k určení požadovaných další řetězec obsahující informace, jako je název sestavení nebo jiné informace.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="8dd1d-117">A <xref:System.Activities.WorkflowIdentity> je jedinečný, pokud jsou některé jeho vlastnosti tři liší od jiného <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8dd1d-118">A <xref:System.Activities.WorkflowIdentity> nesmí obsahovat žádné identifikovatelné osobní údaje (PII).</span><span class="sxs-lookup"><span data-stu-id="8dd1d-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="8dd1d-119">Informace o <xref:System.Activities.WorkflowIdentity> použít k vytvoření instance je pro všechny nakonfigurované sledování životního cyklu služeb v několika různých místech aktivity vygenerované modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="8dd1d-120">WF sledování nemá žádný mechanismus skrýt PII (citlivé uživatelských dat).</span><span class="sxs-lookup"><span data-stu-id="8dd1d-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="8dd1d-121">Proto <xref:System.Activities.WorkflowIdentity> instance nesmí obsahovat žádná data PII tak, jak bude vygenerované modulem runtime v sledování záznamů a mohou být viditelná pro každý, kdo má přístup k zobrazení záznamů sledování.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
 <span data-ttu-id="8dd1d-122">V následujícím příkladu <xref:System.Activities.WorkflowIdentity> se vytvoří a přidružené k instanci pracovního postupu vytvořený `MortgageWorkflow` definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>  
  
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
  
 <span data-ttu-id="8dd1d-123">Při opětovném načtení a obnovení pracovního postupu, <xref:System.Activities.WorkflowIdentity> nakonfigurovaný tak, aby odpovídala <xref:System.Activities.WorkflowIdentity> trvalou pracovního postupu instance musí být použita.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="8dd1d-124">Pokud <xref:System.Activities.WorkflowIdentity> používá při opětovném načtení instance pracovního postupu neodpovídá trvalou <xref:System.Activities.WorkflowIdentity>, <xref:System.Activities.VersionMismatchException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="8dd1d-125">V následujícím příkladu je pokusu o načtení probíhají `MortgageWorkflow` instanci, která byla v předchozím příkladu jako trvalý.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="8dd1d-126">Tato zatížení pokus se uskuteční pomocí <xref:System.Activities.WorkflowIdentity> nakonfigurovaný pro novější verzi hypotéční pracovního postupu, který neodpovídá trvalou instanci.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="8dd1d-127">Při spuštění předchozího kódu, následující <xref:System.Activities.VersionMismatchException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>  
  
 <span data-ttu-id="8dd1d-128">**WorkflowIdentity ('MortgageWorkflow v1; Verze = 1.0.0.0') načíst instance neodpovídá WorkflowIdentity ('MortgageWorkflow v2; Verze = 2.0.0.0') z definice pracovního postupu zadané. Instanci lze načíst pomocí jiné definice nebo aktualizovat pomocí dynamické aktualizace.**</span><span class="sxs-lookup"><span data-stu-id="8dd1d-128">**The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.**</span></span>  
###  <a name="SxS"></a><span data-ttu-id="8dd1d-129">Pomocí WorkflowIdentity spuštění vedle sebe</span><span class="sxs-lookup"><span data-stu-id="8dd1d-129">Side-by-side Execution using WorkflowIdentity</span></span>  
 <span data-ttu-id="8dd1d-130"><xref:System.Activities.WorkflowIdentity>můžete ji použít pro usnadnění provádění více verzí pracovní postup-souběžného.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-130"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="8dd1d-131">Jeden běžný scénář mění obchodní požadavky na dlouhodobé pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-131">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="8dd1d-132">Velký počet instancí pracovního postupu může být spuštěn při nasazení aktualizované verze.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-132">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="8dd1d-133">Hostitelskou aplikaci může být konfigurovaná pro použití definice aktualizované pracovního postupu při spouštění nové instance a je zodpovědností hostitelskou aplikaci můžete při obnovení instance definice pracovního postupu správné.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-133">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="8dd1d-134"><xref:System.Activities.WorkflowIdentity>slouží k identifikaci a zadejte odpovídající definice pracovního postupu při obnovení instancí pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-134"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>  
  
 <span data-ttu-id="8dd1d-135">Načíst <xref:System.Activities.WorkflowIdentity> instance trvalou pracovního postupu, <xref:System.Activities.WorkflowApplication.GetInstance%2A> metoda se používá.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-135">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="8dd1d-136"><xref:System.Activities.WorkflowApplication.GetInstance%2A> Metoda trvá <xref:System.Activities.WorkflowApplication.Id%2A> instance trvalou pracovního postupu a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> který obsahuje trvalý instanci a vrátí <xref:System.Activities.WorkflowApplicationInstance>.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-136">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="8dd1d-137">A <xref:System.Activities.WorkflowApplicationInstance> obsahuje informace o instanci trvalou pracovního postupu, včetně přidružené <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-137">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="8dd1d-138">To přidružené <xref:System.Activities.WorkflowIdentity> lze použít pro hostitele k poskytování definice pracovního postupu správné načítání a obnovení k instanci pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-138">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dd1d-139">Null <xref:System.Activities.WorkflowIdentity> je platný a můžete použít pro hostitele k mapování instancí, které byly nastavené jako trvalé bez přidružené <xref:System.Activities.WorkflowIdentity> k definici správné pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-139">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="8dd1d-140">Tato situace může nastat, když aplikace pracovního postupu nebyla původně zapsána s pracovní postup správy verzí, nebo když je aplikace upgradovali z [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8dd1d-140">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8dd1d-141">[Upgrade rozhraní .NET Framework 4 trvalost databáze podporující pracovní postup správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="8dd1d-141"> [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>  
  
 <span data-ttu-id="8dd1d-142">V následujícím příkladu `Dictionary<WorkflowIdentity, Activity>` je použito k přidružení <xref:System.Activities.WorkflowIdentity> pomocí je spuštěna instance s jejich odpovídající definice pracovního postupu a pracovní postup `MortgageWorkflow` definice pracovního postupu, který je přidružen `identityV1` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-142">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
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
  
 <span data-ttu-id="8dd1d-143">V následujícím příkladu je načíst informace o instanci trvalou pracovního postupu z předchozího příkladu voláním <xref:System.Activities.WorkflowApplication.GetInstance%2A>a trvalou <xref:System.Activities.WorkflowIdentity> informace slouží k načtení odpovídající definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-143">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="8dd1d-144">Tyto informace slouží ke konfiguraci <xref:System.Activities.WorkflowApplication>, a pak je načtena pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-144">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="8dd1d-145">Všimněte si, že vzhledem k tomu, <xref:System.Activities.WorkflowApplication.Load%2A> přetížení, které přijímá <xref:System.Activities.WorkflowApplicationInstance> se používá, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> který byl nakonfigurován na <xref:System.Activities.WorkflowApplicationInstance> je používán <xref:System.Activities.WorkflowApplication> a proto jeho <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost není nutné nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-145">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dd1d-146">Pokud <xref:System.Activities.WorkflowApplication.InstanceStore%2A> vlastnost nastavena, je nutné ji nastavit pomocí stejné <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instanci použitou <xref:System.Activities.WorkflowApplicationInstance> jinak <xref:System.ArgumentException> bude vyvolána s následující zprávou: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-146">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>  
  
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
  
##  <a name="UpdatingWF4PersistenceDatabases"></a><span data-ttu-id="8dd1d-147">Upgrade rozhraní .NET Framework 4 trvalost databáze podporující pracovní postup správy verzí</span><span class="sxs-lookup"><span data-stu-id="8dd1d-147">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>  
 <span data-ttu-id="8dd1d-148">SqlWorkflowInstanceStoreSchemaUpgrade.sql databázového skriptu je zadán pro upgrade trvalost databází vytvořených přes [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] databáze skripty.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-148">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] database scripts.</span></span> <span data-ttu-id="8dd1d-149">Tento skript aktualizace databáze podporují nové možnosti správy verzí, počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8dd1d-149">This script updates the databases to support the new versioning capabilities introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="8dd1d-150">Všechny instance pracovního postupu trvalý v databázích mají výchozí hodnoty verze a můžete pak podílet na spuštění vedle sebe a dynamické aktualizace.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-150">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>  
  
 <span data-ttu-id="8dd1d-151">Pokud [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pracovní postup aplikace pokusí žádné trvalost operace, které používají nové funkce správy verzí v trvalost databázi, která nebyla upgradována, pomocí poskytnutého skriptu <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> je vyvolána s zpráva podobná následující zpráva.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-151">If a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>  
  
 <span data-ttu-id="8dd1d-152">**SqlWorkflowInstanceStore má verzi databáze, 4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' nelze spustit pro tuto verzi databáze.  Upgradujte databázi na '4.5.0.0'.**</span><span class="sxs-lookup"><span data-stu-id="8dd1d-152">**The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.**</span></span>  
###  <a name="ToUpgrade"></a><span data-ttu-id="8dd1d-153">Aktualizace schématu databáze</span><span class="sxs-lookup"><span data-stu-id="8dd1d-153">To upgrade the database schema</span></span>  
  
1.  <span data-ttu-id="8dd1d-154">Otevřete aplikaci SQL Server Management Studio a připojte se k serveru databáze trvalost například **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-154">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>  
  
2.  <span data-ttu-id="8dd1d-155">Zvolte **otevřete**, **soubor** z **souboru** nabídky.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-155">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="8dd1d-156">Přejděte do následující složky:`C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="8dd1d-156">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span></span>  
  
3.  <span data-ttu-id="8dd1d-157">Vyberte **SqlWorkflowInstanceStoreSchemaUpgrade.sql** a klikněte na tlačítko **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-157">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>  
  
4.  <span data-ttu-id="8dd1d-158">Vyberte název databáze trvalost v **dostupné databáze** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-158">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>  
  
5.  <span data-ttu-id="8dd1d-159">Zvolte **Execute** z **dotazu** nabídky.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-159">Choose **Execute** from the **Query** menu.</span></span>  
  
 <span data-ttu-id="8dd1d-160">Po dokončení dotazu je upgradována schématu databáze, a v případě potřeby můžete zobrazit výchozí identitu pracovního postupu, který byl přiřazen k instancím trvalou pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-160">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="8dd1d-161">Trvalost databázi v rozšířit **databáze** uzlu **Průzkumník objektů**a potom rozbalte **zobrazení** uzlu.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-161">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="8dd1d-162">Klikněte pravým tlačítkem na **System.Activities.DurableInstancing.Instances** a zvolte **vyberte Top 1000 řádky**.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-162">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="8dd1d-163">Přejděte na konec sloupců a Všimněte si, že jsou šesti další sloupce, které jsou přidané do zobrazení: **IdentityName**, **IdentityPackage**, **sestavení**, **hlavní** , **Menší**, a **revize**.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-163">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="8dd1d-164">Žádný trvalou pracovní postup bude mít hodnotu **NULL** pro tato pole představující identity hodnotu null. pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="8dd1d-164">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
