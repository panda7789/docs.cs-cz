---
title: '&lt;workflowRuntime&gt;'
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 5560d74a5c69a01a2e05d4c2461a280244e4cd0d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580613"
---
# <a name="ltworkflowruntimegt"></a><span data-ttu-id="d1fed-102">&lt;workflowRuntime&gt;</span><span class="sxs-lookup"><span data-stu-id="d1fed-102">&lt;workflowRuntime&gt;</span></span>
<span data-ttu-id="d1fed-103">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služby Windows Communication Foundation (WCF) založené na pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="d1fed-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="d1fed-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d1fed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d1fed-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d1fed-105">\<behaviors></span></span>  
<span data-ttu-id="d1fed-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d1fed-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d1fed-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d1fed-107">\<behavior></span></span>  
<span data-ttu-id="d1fed-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="d1fed-108">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1fed-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1fed-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1fed-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d1fed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d1fed-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d1fed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1fed-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d1fed-112">Attributes</span></span>  
  
|<span data-ttu-id="d1fed-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d1fed-113">Attribute</span></span>|<span data-ttu-id="d1fed-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d1fed-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1fed-115">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="d1fed-115">cachedInstanceExpiration</span></span>|<span data-ttu-id="d1fed-116">Volitelně <xref:System.TimeSpan> hodnotu, která určuje maximální dobu setrvání instance pracovního postupu v paměti ve stavu nečinnosti, než je nuceným uvolněním nebo přerušením.</span><span class="sxs-lookup"><span data-stu-id="d1fed-116">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="d1fed-117">Pokud má aktivity typu workflowruntime `PersistenceService` které provádí unloadOnIdle, tento atribut se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="d1fed-117">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="d1fed-118">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="d1fed-118">enablePerformanceCounters</span></span>|<span data-ttu-id="d1fed-119">Volitelná logická hodnota, která určuje, zda jsou povoleny čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="d1fed-119">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="d1fed-120">Čítače výkonu poskytují informace o různých statistiky týkající se pracovní postup, ale mohou způsobit snížení výkonu při spuštění modulu runtime pracovního postupu, a pokud jsou spuštěny instance pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="d1fed-120">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="d1fed-121">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="d1fed-121">The default value is `true`.</span></span>|  
|<span data-ttu-id="d1fed-122">name</span><span class="sxs-lookup"><span data-stu-id="d1fed-122">name</span></span>|<span data-ttu-id="d1fed-123">Řetězec obsahující název modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d1fed-123">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="d1fed-124">Název se používá ve výstupu k rozlišení tohoto modulu runtime z jiných modulů runtime, který může běžet na systému, například v čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="d1fed-124">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="d1fed-125">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="d1fed-125">The default is an empty string.</span></span>|  
|<span data-ttu-id="d1fed-126">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="d1fed-126">validateOnCreate</span></span>|<span data-ttu-id="d1fed-127">Volitelná logická hodnota, která určuje, zda ověření definice pracovního postupu dojde při otevření WorkflowServiceHost provedeno.</span><span class="sxs-lookup"><span data-stu-id="d1fed-127">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="d1fed-128">Když tento atribut je nastaven na `true`, provádí se ověření pracovního postupu pokaždé, když `WorkflowServiceHost.Open` je volána.</span><span class="sxs-lookup"><span data-stu-id="d1fed-128">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="d1fed-129">Pokud byly zjištěny chyby ověřování, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> , je vržena chyba.</span><span class="sxs-lookup"><span data-stu-id="d1fed-129">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="d1fed-130">Pokud je tato vlastnost nastavena na `false`, stane se žádné ověření definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="d1fed-130">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="d1fed-131">Výchozí hodnota této vlastnosti je `true`.</span><span class="sxs-lookup"><span data-stu-id="d1fed-131">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1fed-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d1fed-132">Child Elements</span></span>  
  
|<span data-ttu-id="d1fed-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="d1fed-133">Element</span></span>|<span data-ttu-id="d1fed-134">Popis</span><span class="sxs-lookup"><span data-stu-id="d1fed-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1fed-135">commonParameters</span><span class="sxs-lookup"><span data-stu-id="d1fed-135">commonParameters</span></span>|<span data-ttu-id="d1fed-136">Kolekce společných parametrů, které jsou používané službami.</span><span class="sxs-lookup"><span data-stu-id="d1fed-136">A collection of common parameters used by services.</span></span> <span data-ttu-id="d1fed-137">Tato kolekce bude obvykle obsahují řetězec připojení k databázi, kterou může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="d1fed-137">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="d1fed-138">služby</span><span class="sxs-lookup"><span data-stu-id="d1fed-138">services</span></span>|<span data-ttu-id="d1fed-139">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modul.</span><span class="sxs-lookup"><span data-stu-id="d1fed-139">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="d1fed-140">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d1fed-140">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="d1fed-141">Služby uvedené v kolekci inicializoval modul runtime pracovního postupu, který se přidá do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d1fed-141">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="d1fed-142">Proto služby uvedené v kolekci musí následovat některá pravidla týkající se podpisy jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="d1fed-142">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="d1fed-143">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d1fed-143">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1fed-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d1fed-144">Parent Elements</span></span>  
  
|<span data-ttu-id="d1fed-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="d1fed-145">Element</span></span>|<span data-ttu-id="d1fed-146">Popis</span><span class="sxs-lookup"><span data-stu-id="d1fed-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1fed-147">\<behavior></span><span class="sxs-lookup"><span data-stu-id="d1fed-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d1fed-148">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="d1fed-148">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1fed-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1fed-149">Remarks</span></span>  
 <span data-ttu-id="d1fed-150">Další informace o použití konfiguračního souboru pro řízení chování <xref:System.Workflow.Runtime.WorkflowRuntime> objekt hostitele aplikace Windows Workflow Foundation, najdete v článku [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d1fed-150">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1fed-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1fed-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d1fed-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1fed-152">See also</span></span>
- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="d1fed-153">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d1fed-153">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
