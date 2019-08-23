---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 0cd04f66cc4b73eb5f1c43bd6c8dc9189dfceff1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915220"
---
# <a name="workflowruntime"></a><span data-ttu-id="2ee10-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="2ee10-101">\<workflowRuntime></span></span>
<span data-ttu-id="2ee10-102">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).</span><span class="sxs-lookup"><span data-stu-id="2ee10-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="2ee10-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2ee10-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2ee10-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="2ee10-104">\<behaviors></span></span>  
<span data-ttu-id="2ee10-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2ee10-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="2ee10-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="2ee10-106">\<behavior></span></span>  
<span data-ttu-id="2ee10-107">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="2ee10-107">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee10-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ee10-108">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ee10-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ee10-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2ee10-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ee10-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ee10-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ee10-111">Attributes</span></span>  
  
|<span data-ttu-id="2ee10-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2ee10-112">Attribute</span></span>|<span data-ttu-id="2ee10-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2ee10-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ee10-114">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="2ee10-114">cachedInstanceExpiration</span></span>|<span data-ttu-id="2ee10-115">Volitelná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou může instance pracovního postupu zůstat v paměti ve stavu nečinnosti, než bude vynuceně uvolněna nebo přerušena.</span><span class="sxs-lookup"><span data-stu-id="2ee10-115">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="2ee10-116">Pokud je v aktivitě typu WorkflowRuntime `PersistenceService` proveden UnloadOnIdle, tento atribut se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="2ee10-116">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="2ee10-117">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="2ee10-117">enablePerformanceCounters</span></span>|<span data-ttu-id="2ee10-118">Volitelná logická hodnota, která určuje, zda jsou povoleny čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="2ee10-118">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="2ee10-119">Čítače výkonu poskytují informace o různých statistikách vztahujících se k pracovním postupům, ale způsobují snížení výkonu při spuštění modulu runtime pracovního postupu a při spuštěných instancích pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2ee10-119">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="2ee10-120">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="2ee10-120">The default value is `true`.</span></span>|  
|<span data-ttu-id="2ee10-121">name</span><span class="sxs-lookup"><span data-stu-id="2ee10-121">name</span></span>|<span data-ttu-id="2ee10-122">Řetězec, který obsahuje název modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2ee10-122">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="2ee10-123">Název se používá ve výstupu k odlišení tohoto modulu runtime od jiných modulů runtime, které mohou být spuštěny v systému, například v čítačích výkonu.</span><span class="sxs-lookup"><span data-stu-id="2ee10-123">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="2ee10-124">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2ee10-124">The default is an empty string.</span></span>|  
|<span data-ttu-id="2ee10-125">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="2ee10-125">validateOnCreate</span></span>|<span data-ttu-id="2ee10-126">Volitelná logická hodnota, která určuje, zda bude při otevření hostitele WorkflowServiceHost provedeno ověření definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2ee10-126">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="2ee10-127">Pokud je tento atribut nastaven na `true`, je provedeno ověření pracovního postupu při `WorkflowServiceHost.Open` každém volání.</span><span class="sxs-lookup"><span data-stu-id="2ee10-127">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="2ee10-128">Pokud jsou nalezeny chyby ověřování, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="2ee10-128">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="2ee10-129">Pokud je tato vlastnost nastavena na `false`hodnotu, nebude provedena žádná validace definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2ee10-129">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="2ee10-130">Výchozí hodnota této vlastnosti je `true`.</span><span class="sxs-lookup"><span data-stu-id="2ee10-130">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ee10-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ee10-131">Child Elements</span></span>  
  
|<span data-ttu-id="2ee10-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ee10-132">Element</span></span>|<span data-ttu-id="2ee10-133">Popis</span><span class="sxs-lookup"><span data-stu-id="2ee10-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ee10-134">commonParameters</span><span class="sxs-lookup"><span data-stu-id="2ee10-134">commonParameters</span></span>|<span data-ttu-id="2ee10-135">Kolekce běžných parametrů používaných službami.</span><span class="sxs-lookup"><span data-stu-id="2ee10-135">A collection of common parameters used by services.</span></span> <span data-ttu-id="2ee10-136">Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="2ee10-136">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="2ee10-137">služby</span><span class="sxs-lookup"><span data-stu-id="2ee10-137">services</span></span>|<span data-ttu-id="2ee10-138">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modulu.</span><span class="sxs-lookup"><span data-stu-id="2ee10-138">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="2ee10-139">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2ee10-139">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="2ee10-140">Služby zadané v kolekci budou inicializovány modulem runtime pracovního postupu a přidány ke svým službám při volání příslušného <xref:System.Workflow.Runtime.WorkflowRuntime> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="2ee10-140">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="2ee10-141">Proto musí služby zadané v kolekci dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="2ee10-141">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="2ee10-142">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2ee10-142">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2ee10-143">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ee10-143">Parent Elements</span></span>  
  
|<span data-ttu-id="2ee10-144">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ee10-144">Element</span></span>|<span data-ttu-id="2ee10-145">Popis</span><span class="sxs-lookup"><span data-stu-id="2ee10-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ee10-146">\<> chování</span><span class="sxs-lookup"><span data-stu-id="2ee10-146">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2ee10-147">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2ee10-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ee10-148">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ee10-148">Remarks</span></span>  
 <span data-ttu-id="2ee10-149">Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2ee10-149">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ee10-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ee10-150">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="2ee10-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ee10-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="2ee10-152">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2ee10-152">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
