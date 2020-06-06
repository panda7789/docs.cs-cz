---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: d12656b77fa219080382603fd04a542d2fa9064a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399078"
---
# \<workflowRuntime>
<span data-ttu-id="78e50-101">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).</span><span class="sxs-lookup"><span data-stu-id="78e50-101">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a><span data-ttu-id="78e50-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78e50-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78e50-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="78e50-103">Attributes and Elements</span></span>  
 <span data-ttu-id="78e50-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="78e50-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78e50-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="78e50-105">Attributes</span></span>  
  
|<span data-ttu-id="78e50-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="78e50-106">Attribute</span></span>|<span data-ttu-id="78e50-107">Popis</span><span class="sxs-lookup"><span data-stu-id="78e50-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78e50-108">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="78e50-108">cachedInstanceExpiration</span></span>|<span data-ttu-id="78e50-109">Volitelná <xref:System.TimeSpan> hodnota, která určuje maximální dobu, po kterou může instance pracovního postupu zůstat v paměti ve stavu nečinnosti, než bude vynuceně uvolněna nebo přerušena.</span><span class="sxs-lookup"><span data-stu-id="78e50-109">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="78e50-110">Pokud je v aktivitě typu WorkflowRuntime `PersistenceService` proveden UnloadOnIdle, tento atribut se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="78e50-110">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="78e50-111">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="78e50-111">enablePerformanceCounters</span></span>|<span data-ttu-id="78e50-112">Volitelná logická hodnota, která určuje, zda jsou povoleny čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="78e50-112">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="78e50-113">Čítače výkonu poskytují informace o různých statistikách vztahujících se k pracovním postupům, ale způsobují snížení výkonu při spuštění modulu runtime pracovního postupu a při spuštěných instancích pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="78e50-113">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="78e50-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="78e50-114">The default value is `true`.</span></span>|  
|<span data-ttu-id="78e50-115">name</span><span class="sxs-lookup"><span data-stu-id="78e50-115">name</span></span>|<span data-ttu-id="78e50-116">Řetězec, který obsahuje název modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="78e50-116">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="78e50-117">Název se používá ve výstupu k odlišení tohoto modulu runtime od jiných modulů runtime, které mohou být spuštěny v systému, například v čítačích výkonu.</span><span class="sxs-lookup"><span data-stu-id="78e50-117">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="78e50-118">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="78e50-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="78e50-119">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="78e50-119">validateOnCreate</span></span>|<span data-ttu-id="78e50-120">Volitelná logická hodnota, která určuje, zda bude při otevření hostitele WorkflowServiceHost provedeno ověření definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="78e50-120">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="78e50-121">Pokud je tento atribut nastaven na `true` , je provedeno ověření pracovního postupu při každém `WorkflowServiceHost.Open` volání.</span><span class="sxs-lookup"><span data-stu-id="78e50-121">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="78e50-122">Pokud jsou nalezeny chyby ověřování, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> je vyvolána chyba.</span><span class="sxs-lookup"><span data-stu-id="78e50-122">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="78e50-123">Pokud je tato vlastnost nastavena na hodnotu `false` , nebude provedena žádná validace definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="78e50-123">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="78e50-124">Výchozí hodnota této vlastnosti je `true` .</span><span class="sxs-lookup"><span data-stu-id="78e50-124">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78e50-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="78e50-125">Child Elements</span></span>  
  
|<span data-ttu-id="78e50-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="78e50-126">Element</span></span>|<span data-ttu-id="78e50-127">Description</span><span class="sxs-lookup"><span data-stu-id="78e50-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78e50-128">commonParameters</span><span class="sxs-lookup"><span data-stu-id="78e50-128">commonParameters</span></span>|<span data-ttu-id="78e50-129">Kolekce běžných parametrů používaných službami.</span><span class="sxs-lookup"><span data-stu-id="78e50-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="78e50-130">Tato kolekce obvykle zahrnuje připojovací řetězec databáze, který může sdílet trvalé služby.</span><span class="sxs-lookup"><span data-stu-id="78e50-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="78e50-131">services</span><span class="sxs-lookup"><span data-stu-id="78e50-131">services</span></span>|<span data-ttu-id="78e50-132">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modulu.</span><span class="sxs-lookup"><span data-stu-id="78e50-132">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="78e50-133">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="78e50-133">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="78e50-134">Služby zadané v kolekci budou inicializovány modulem runtime pracovního postupu a přidány ke svým službám při <xref:System.Workflow.Runtime.WorkflowRuntime> volání příslušného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="78e50-134">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="78e50-135">Proto musí služby zadané v kolekci dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="78e50-135">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="78e50-136">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="78e50-136">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78e50-137">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="78e50-137">Parent Elements</span></span>  
  
|<span data-ttu-id="78e50-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="78e50-138">Element</span></span>|<span data-ttu-id="78e50-139">Description</span><span class="sxs-lookup"><span data-stu-id="78e50-139">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="78e50-140">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="78e50-140">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78e50-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78e50-141">Remarks</span></span>  
 <span data-ttu-id="78e50-142">Další informace o tom, jak pomocí konfiguračního souboru řídit chování <xref:System.Workflow.Runtime.WorkflowRuntime> objektu programovací model Windows Workflow Foundation hostitelské aplikace, najdete v tématu [konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="78e50-142">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78e50-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="78e50-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="78e50-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="78e50-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="78e50-145">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="78e50-145">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
