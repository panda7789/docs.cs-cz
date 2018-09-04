---
title: '&lt;add&gt; – &lt;services&gt;'
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 6aa903d4188d108940c76ac50eb0a706fbea8f8b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530247"
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="b1328-102">&lt;add&gt; – &lt;services&gt;</span><span class="sxs-lookup"><span data-stu-id="b1328-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="b1328-103">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služby Windows Communication Foundation (WCF) založené na pracovních postupech.</span><span class="sxs-lookup"><span data-stu-id="b1328-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="b1328-104">Tento prvek je typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b1328-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="b1328-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b1328-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b1328-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b1328-106">\<behaviors></span></span>  
<span data-ttu-id="b1328-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b1328-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="b1328-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="b1328-108">\<behavior></span></span>  
<span data-ttu-id="b1328-109">\<služby ></span><span class="sxs-lookup"><span data-stu-id="b1328-109">\<services></span></span>  
<span data-ttu-id="b1328-110">\<add></span><span class="sxs-lookup"><span data-stu-id="b1328-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1328-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1328-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1328-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1328-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b1328-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1328-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1328-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1328-114">Attributes</span></span>  
  
|<span data-ttu-id="b1328-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="b1328-115">Attribute</span></span>|<span data-ttu-id="b1328-116">Popis</span><span class="sxs-lookup"><span data-stu-id="b1328-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1328-117">– typ</span><span class="sxs-lookup"><span data-stu-id="b1328-117">type</span></span>|<span data-ttu-id="b1328-118">Řetězec určující název typu kvalifikovaného pro sestavení služby mají být inicializovány.</span><span class="sxs-lookup"><span data-stu-id="b1328-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="b1328-119">Zadaná služba musí dodržovat určitá pravidla o podpisech jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="b1328-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="b1328-120">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b1328-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1328-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1328-121">Child Elements</span></span>  
 <span data-ttu-id="b1328-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="b1328-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1328-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1328-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b1328-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1328-124">Element</span></span>|<span data-ttu-id="b1328-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b1328-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1328-126">\<služby ></span><span class="sxs-lookup"><span data-stu-id="b1328-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="b1328-127">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modul.</span><span class="sxs-lookup"><span data-stu-id="b1328-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="b1328-128">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b1328-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="b1328-129">Služby uvedené v kolekci inicializoval modul runtime pracovního postupu, který se přidá do jeho služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="b1328-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="b1328-130">Proto služby uvedené v kolekci musí následovat některá pravidla týkající se podpisy jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="b1328-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="b1328-131">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b1328-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1328-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1328-132">Remarks</span></span>  
 <span data-ttu-id="b1328-133">Služba zadaná v tomto elementu se inicializovat modul runtime pracovního postupu a přidat do své služby při odpovídající <xref:System.Workflow.Runtime.WorkflowRuntime> volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="b1328-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="b1328-134">Zadaná služba, proto musí následovat některá pravidla týkající se podpisy jejich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="b1328-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="b1328-135">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b1328-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1328-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1328-136">Example</span></span>  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1328-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1328-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <span data-ttu-id="b1328-138">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b1328-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
