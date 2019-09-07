---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: d12656b77fa219080382603fd04a542d2fa9064a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399078"
---
# <a name="workflowruntime"></a><span data-ttu-id="c5cd9-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="c5cd9-101">\<workflowRuntime></span></span>
<span data-ttu-id="c5cd9-102">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).</span><span class="sxs-lookup"><span data-stu-id="c5cd9-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
<span data-ttu-id="c5cd9-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c5cd9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c5cd9-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c5cd9-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c5cd9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c5cd9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c5cd9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c5cd9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c5cd9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c5cd9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c5cd9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> aktivity typu workflowRuntime**</span><span class="sxs-lookup"><span data-stu-id="c5cd9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5cd9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5cd9-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5cd9-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c5cd9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c5cd9-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5cd9-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c5cd9-112">Attributes</span></span>  
  
|<span data-ttu-id="c5cd9-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c5cd9-113">Attribute</span></span>|<span data-ttu-id="c5cd9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c5cd9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5cd9-115">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="c5cd9-115">cachedInstanceExpiration</span></span>|<span data-ttu-id="c5cd9-116">Volitelná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou může instance pracovního postupu zůstat v paměti ve stavu nečinnosti, než bude vynuceně uvolněna nebo přerušena.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-116">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="c5cd9-117">Pokud je v aktivitě typu WorkflowRuntime `PersistenceService` proveden UnloadOnIdle, tento atribut se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-117">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="c5cd9-118">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="c5cd9-118">enablePerformanceCounters</span></span>|<span data-ttu-id="c5cd9-119">Volitelná logická hodnota, která určuje, zda jsou povoleny čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-119">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="c5cd9-120">Čítače výkonu poskytují informace o různých statistikách vztahujících se k pracovním postupům, ale způsobují snížení výkonu při spuštění modulu runtime pracovního postupu a při spuštěných instancích pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-120">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="c5cd9-121">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-121">The default value is `true`.</span></span>|  
|<span data-ttu-id="c5cd9-122">name</span><span class="sxs-lookup"><span data-stu-id="c5cd9-122">name</span></span>|<span data-ttu-id="c5cd9-123">Řetězec, který obsahuje název modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-123">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="c5cd9-124">Název se používá ve výstupu k odlišení tohoto modulu runtime od jiných modulů runtime, které mohou být spuštěny v systému, například v čítačích výkonu.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-124">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="c5cd9-125">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-125">The default is an empty string.</span></span>|  
|<span data-ttu-id="c5cd9-126">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="c5cd9-126">validateOnCreate</span></span>|<span data-ttu-id="c5cd9-127">Volitelná logická hodnota, která určuje, zda bude při otevření hostitele WorkflowServiceHost provedeno ověření definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-127">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="c5cd9-128">Pokud je tento atribut nastaven na `true`, je provedeno ověření pracovního postupu při `WorkflowServiceHost.Open` každém volání.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-128">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="c5cd9-129">Pokud jsou nalezeny chyby ověřování, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-129">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="c5cd9-130">Pokud je tato vlastnost nastavena na `false`hodnotu, nebude provedena žádná validace definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-130">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="c5cd9-131">Výchozí hodnota této vlastnosti je `true`.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-131">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5cd9-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c5cd9-132">Child Elements</span></span>  
  
|<span data-ttu-id="c5cd9-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="c5cd9-133">Element</span></span>|<span data-ttu-id="c5cd9-134">Popis</span><span class="sxs-lookup"><span data-stu-id="c5cd9-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5cd9-135">commonParameters</span><span class="sxs-lookup"><span data-stu-id="c5cd9-135">commonParameters</span></span>|<span data-ttu-id="c5cd9-136">Kolekce běžných parametrů používaných službami.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-136">A collection of common parameters used by services.</span></span> <span data-ttu-id="c5cd9-137">Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-137">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="c5cd9-138">služby</span><span class="sxs-lookup"><span data-stu-id="c5cd9-138">services</span></span>|<span data-ttu-id="c5cd9-139">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modulu.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-139">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="c5cd9-140">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-140">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="c5cd9-141">Služby zadané v kolekci budou inicializovány modulem runtime pracovního postupu a přidány ke svým službám při volání příslušného <xref:System.Workflow.Runtime.WorkflowRuntime> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-141">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="c5cd9-142">Proto musí služby zadané v kolekci dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-142">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="c5cd9-143">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-143">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5cd9-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c5cd9-144">Parent Elements</span></span>  
  
|<span data-ttu-id="c5cd9-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="c5cd9-145">Element</span></span>|<span data-ttu-id="c5cd9-146">Popis</span><span class="sxs-lookup"><span data-stu-id="c5cd9-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5cd9-147">\<> chování</span><span class="sxs-lookup"><span data-stu-id="c5cd9-147">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c5cd9-148">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="c5cd9-148">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5cd9-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5cd9-149">Remarks</span></span>  
 <span data-ttu-id="c5cd9-150">Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c5cd9-150">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5cd9-151">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5cd9-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5cd9-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5cd9-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="c5cd9-153">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c5cd9-153">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
