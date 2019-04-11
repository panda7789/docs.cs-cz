---
title: <add> of <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: c07b3377db4f5b434fd021b09de510c1d43ec832
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219184"
---
# <a name="add-of-services"></a><span data-ttu-id="19d6a-102">\<Přidat > z \<služby ></span><span class="sxs-lookup"><span data-stu-id="19d6a-102">\<add> of \<services></span></span>
<span data-ttu-id="19d6a-103">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služby Windows Communication Foundation (WCF) založené na pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="19d6a-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="19d6a-104">Tento prvek je typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="19d6a-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="19d6a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="19d6a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="19d6a-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="19d6a-106">\<behaviors></span></span>  
<span data-ttu-id="19d6a-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="19d6a-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="19d6a-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="19d6a-108">\<behavior></span></span>  
<span data-ttu-id="19d6a-109">\<services></span><span class="sxs-lookup"><span data-stu-id="19d6a-109">\<services></span></span>  
<span data-ttu-id="19d6a-110">\<add></span><span class="sxs-lookup"><span data-stu-id="19d6a-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19d6a-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19d6a-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19d6a-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="19d6a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="19d6a-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="19d6a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19d6a-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="19d6a-114">Attributes</span></span>  
  
|<span data-ttu-id="19d6a-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="19d6a-115">Attribute</span></span>|<span data-ttu-id="19d6a-116">Popis</span><span class="sxs-lookup"><span data-stu-id="19d6a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19d6a-117"> – typ</span><span class="sxs-lookup"><span data-stu-id="19d6a-117">type</span></span>|<span data-ttu-id="19d6a-118">Řetězec určující název typu kvalifikovaného pro sestavení služby mají být inicializovány.</span><span class="sxs-lookup"><span data-stu-id="19d6a-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="19d6a-119">Zadaná služba musí dodržovat určitá pravidla o podpisech jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="19d6a-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="19d6a-120">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="19d6a-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19d6a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="19d6a-121">Child Elements</span></span>  
 <span data-ttu-id="19d6a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="19d6a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19d6a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="19d6a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="19d6a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="19d6a-124">Element</span></span>|<span data-ttu-id="19d6a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="19d6a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19d6a-126">\<services></span><span class="sxs-lookup"><span data-stu-id="19d6a-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="19d6a-127">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modul.</span><span class="sxs-lookup"><span data-stu-id="19d6a-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="19d6a-128">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="19d6a-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="19d6a-129">Služby uvedené v kolekci inicializoval modul runtime pracovního postupu, který se přidá do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="19d6a-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="19d6a-130">Proto služby uvedené v kolekci musí následovat některá pravidla týkající se podpisy jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="19d6a-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="19d6a-131">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="19d6a-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19d6a-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19d6a-132">Remarks</span></span>  
 <span data-ttu-id="19d6a-133">Služba zadaná v tomto elementu se inicializovat modul runtime pracovního postupu a přidat do své služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="19d6a-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="19d6a-134">Zadaná služba, proto musí následovat některá pravidla týkající se podpisy jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="19d6a-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="19d6a-135">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="19d6a-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19d6a-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="19d6a-136">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19d6a-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19d6a-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- [<span data-ttu-id="19d6a-138">Konfigurační soubory pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="19d6a-138">Workflow Configuration Files</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
