---
title: <add> z <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 38dec132626b97accacea1b7007d914edcab0abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926649"
---
# <a name="add-of-services"></a><span data-ttu-id="6651e-102">\<Přidat > \<služeb ></span><span class="sxs-lookup"><span data-stu-id="6651e-102">\<add> of \<services></span></span>
<span data-ttu-id="6651e-103">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).</span><span class="sxs-lookup"><span data-stu-id="6651e-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="6651e-104">Tento prvek je typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="6651e-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="6651e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6651e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6651e-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="6651e-106">\<behaviors></span></span>  
<span data-ttu-id="6651e-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6651e-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="6651e-108">\<> chování</span><span class="sxs-lookup"><span data-stu-id="6651e-108">\<behavior></span></span>  
<span data-ttu-id="6651e-109">\<> služeb</span><span class="sxs-lookup"><span data-stu-id="6651e-109">\<services></span></span>  
<span data-ttu-id="6651e-110">\<add></span><span class="sxs-lookup"><span data-stu-id="6651e-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6651e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6651e-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6651e-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6651e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6651e-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6651e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6651e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="6651e-114">Attributes</span></span>  
  
|<span data-ttu-id="6651e-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="6651e-115">Attribute</span></span>|<span data-ttu-id="6651e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="6651e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6651e-117">– typ</span><span class="sxs-lookup"><span data-stu-id="6651e-117">type</span></span>|<span data-ttu-id="6651e-118">Řetězec, který určuje název typu kvalifikovaného pro sestavení služby, která má být inicializována.</span><span class="sxs-lookup"><span data-stu-id="6651e-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="6651e-119">Zadaná služba musí dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="6651e-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="6651e-120">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="6651e-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6651e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6651e-121">Child Elements</span></span>  
 <span data-ttu-id="6651e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="6651e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6651e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6651e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6651e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="6651e-124">Element</span></span>|<span data-ttu-id="6651e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="6651e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6651e-126">\<services></span><span class="sxs-lookup"><span data-stu-id="6651e-126">\<services></span></span>](services-of-workflowruntime.md)|<span data-ttu-id="6651e-127">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modulu.</span><span class="sxs-lookup"><span data-stu-id="6651e-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="6651e-128">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="6651e-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="6651e-129">Služby zadané v kolekci budou inicializovány modulem runtime pracovního postupu a přidány ke svým službám při volání příslušného <xref:System.Workflow.Runtime.WorkflowRuntime> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6651e-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="6651e-130">Proto musí služby zadané v kolekci dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="6651e-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="6651e-131">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="6651e-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6651e-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6651e-132">Remarks</span></span>  
 <span data-ttu-id="6651e-133">Služba zadaná v tomto elementu bude inicializována modulem runtime pracovního postupu a přidána ke svým službám při volání příslušného <xref:System.Workflow.Runtime.WorkflowRuntime> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6651e-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="6651e-134">Proto je nutné, aby Zadaná služba dodržovala určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="6651e-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="6651e-135">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="6651e-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6651e-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="6651e-136">Example</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="6651e-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6651e-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="6651e-138">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6651e-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
