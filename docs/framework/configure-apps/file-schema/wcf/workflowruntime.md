---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: db5e1083c07d4e204eb19eaae9257ed44439132e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206561"
---
# <a name="workflowruntime"></a><span data-ttu-id="d6b91-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="d6b91-101">\<workflowRuntime></span></span>
<span data-ttu-id="d6b91-102">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služby Windows Communication Foundation (WCF) založené na pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="d6b91-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="d6b91-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d6b91-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d6b91-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d6b91-104">\<behaviors></span></span>  
<span data-ttu-id="d6b91-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d6b91-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="d6b91-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d6b91-106">\<behavior></span></span>  
<span data-ttu-id="d6b91-107">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="d6b91-107">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b91-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6b91-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6b91-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6b91-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d6b91-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6b91-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6b91-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6b91-111">Attributes</span></span>  
  
|<span data-ttu-id="d6b91-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6b91-112">Attribute</span></span>|<span data-ttu-id="d6b91-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b91-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6b91-114">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="d6b91-114">cachedInstanceExpiration</span></span>|<span data-ttu-id="d6b91-115">Volitelně <xref:System.TimeSpan> hodnotu, která určuje maximální dobu setrvání instance pracovního postupu v paměti ve stavu nečinnosti, než je nuceným uvolněním nebo přerušením.</span><span class="sxs-lookup"><span data-stu-id="d6b91-115">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="d6b91-116">Pokud má aktivity typu workflowruntime `PersistenceService` které provádí unloadOnIdle, tento atribut se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="d6b91-116">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="d6b91-117">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="d6b91-117">enablePerformanceCounters</span></span>|<span data-ttu-id="d6b91-118">Volitelná logická hodnota, která určuje, zda jsou povoleny čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="d6b91-118">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="d6b91-119">Čítače výkonu poskytují informace o různých statistiky týkající se pracovní postup, ale mohou způsobit snížení výkonu při spuštění modulu runtime pracovního postupu, a pokud jsou spuštěny instance pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="d6b91-119">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="d6b91-120">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="d6b91-120">The default value is `true`.</span></span>|  
|<span data-ttu-id="d6b91-121">name</span><span class="sxs-lookup"><span data-stu-id="d6b91-121">name</span></span>|<span data-ttu-id="d6b91-122">Řetězec obsahující název modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d6b91-122">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="d6b91-123">Název se používá ve výstupu k rozlišení tohoto modulu runtime z jiných modulů runtime, který může běžet na systému, například v čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="d6b91-123">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="d6b91-124">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="d6b91-124">The default is an empty string.</span></span>|  
|<span data-ttu-id="d6b91-125">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="d6b91-125">validateOnCreate</span></span>|<span data-ttu-id="d6b91-126">Volitelná logická hodnota, která určuje, zda ověření definice pracovního postupu dojde při otevření WorkflowServiceHost provedeno.</span><span class="sxs-lookup"><span data-stu-id="d6b91-126">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="d6b91-127">Když tento atribut je nastaven na `true`, provádí se ověření pracovního postupu pokaždé, když `WorkflowServiceHost.Open` je volána.</span><span class="sxs-lookup"><span data-stu-id="d6b91-127">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="d6b91-128">Pokud byly zjištěny chyby ověřování, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> , je vržena chyba.</span><span class="sxs-lookup"><span data-stu-id="d6b91-128">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="d6b91-129">Pokud je tato vlastnost nastavena na `false`, stane se žádné ověření definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d6b91-129">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="d6b91-130">Výchozí hodnota této vlastnosti je `true`.</span><span class="sxs-lookup"><span data-stu-id="d6b91-130">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6b91-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6b91-131">Child Elements</span></span>  
  
|<span data-ttu-id="d6b91-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6b91-132">Element</span></span>|<span data-ttu-id="d6b91-133">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b91-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6b91-134">commonParameters</span><span class="sxs-lookup"><span data-stu-id="d6b91-134">commonParameters</span></span>|<span data-ttu-id="d6b91-135">Kolekce společných parametrů, které jsou používané službami.</span><span class="sxs-lookup"><span data-stu-id="d6b91-135">A collection of common parameters used by services.</span></span> <span data-ttu-id="d6b91-136">Tato kolekce bude obvykle obsahují řetězec připojení k databázi, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="d6b91-136">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="d6b91-137">služby</span><span class="sxs-lookup"><span data-stu-id="d6b91-137">services</span></span>|<span data-ttu-id="d6b91-138">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modul.</span><span class="sxs-lookup"><span data-stu-id="d6b91-138">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="d6b91-139">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d6b91-139">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="d6b91-140">Služby uvedené v kolekci inicializoval modul runtime pracovního postupu, který se přidá do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d6b91-140">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="d6b91-141">Proto služby uvedené v kolekci musí následovat některá pravidla týkající se podpisy jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="d6b91-141">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="d6b91-142">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d6b91-142">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6b91-143">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6b91-143">Parent Elements</span></span>  
  
|<span data-ttu-id="d6b91-144">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6b91-144">Element</span></span>|<span data-ttu-id="d6b91-145">Popis</span><span class="sxs-lookup"><span data-stu-id="d6b91-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6b91-146">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d6b91-146">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d6b91-147">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="d6b91-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6b91-148">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6b91-148">Remarks</span></span>  
 <span data-ttu-id="d6b91-149">Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v článku [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d6b91-149">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6b91-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6b91-150">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6b91-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6b91-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="d6b91-152">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d6b91-152">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
