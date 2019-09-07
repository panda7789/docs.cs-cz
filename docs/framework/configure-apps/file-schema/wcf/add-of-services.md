---
title: <add> z <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: dc769097a3aede2522c1fa7a4cf8e36c2d8fdfe8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398294"
---
# <a name="add-of-services"></a><span data-ttu-id="9dc91-102">\<Přidat > \<služeb ></span><span class="sxs-lookup"><span data-stu-id="9dc91-102">\<add> of \<services></span></span>
<span data-ttu-id="9dc91-103">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).</span><span class="sxs-lookup"><span data-stu-id="9dc91-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="9dc91-104">Tento prvek je typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9dc91-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
<span data-ttu-id="9dc91-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9dc91-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9dc91-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9dc91-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9dc91-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9dc91-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9dc91-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9dc91-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="9dc91-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9dc91-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="9dc91-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> aktivity typu workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="9dc91-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="9dc91-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services-of-workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="9dc91-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)</span></span>\
<span data-ttu-id="9dc91-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="9dc91-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc91-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dc91-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9dc91-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9dc91-114">Attributes and Elements</span></span>  
 <span data-ttu-id="9dc91-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9dc91-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9dc91-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="9dc91-116">Attributes</span></span>  
  
|<span data-ttu-id="9dc91-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="9dc91-117">Attribute</span></span>|<span data-ttu-id="9dc91-118">Popis</span><span class="sxs-lookup"><span data-stu-id="9dc91-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9dc91-119">– typ</span><span class="sxs-lookup"><span data-stu-id="9dc91-119">type</span></span>|<span data-ttu-id="9dc91-120">Řetězec, který určuje název typu kvalifikovaného pro sestavení služby, která má být inicializována.</span><span class="sxs-lookup"><span data-stu-id="9dc91-120">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="9dc91-121">Zadaná služba musí dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="9dc91-121">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9dc91-122">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9dc91-122">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9dc91-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9dc91-123">Child Elements</span></span>  
 <span data-ttu-id="9dc91-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="9dc91-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9dc91-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9dc91-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9dc91-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="9dc91-126">Element</span></span>|<span data-ttu-id="9dc91-127">Popis</span><span class="sxs-lookup"><span data-stu-id="9dc91-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9dc91-128">\<services></span><span class="sxs-lookup"><span data-stu-id="9dc91-128">\<services></span></span>](services-of-workflowruntime.md)|<span data-ttu-id="9dc91-129">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modulu.</span><span class="sxs-lookup"><span data-stu-id="9dc91-129">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="9dc91-130">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9dc91-130">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="9dc91-131">Služby zadané v kolekci budou inicializovány modulem runtime pracovního postupu a přidány ke svým službám při volání příslušného <xref:System.Workflow.Runtime.WorkflowRuntime> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="9dc91-131">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="9dc91-132">Proto musí služby zadané v kolekci dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="9dc91-132">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9dc91-133">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9dc91-133">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9dc91-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9dc91-134">Remarks</span></span>  
 <span data-ttu-id="9dc91-135">Služba zadaná v tomto elementu bude inicializována modulem runtime pracovního postupu a přidána ke svým službám při volání příslušného <xref:System.Workflow.Runtime.WorkflowRuntime> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="9dc91-135">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="9dc91-136">Proto je nutné, aby Zadaná služba dodržovala určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="9dc91-136">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="9dc91-137">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="9dc91-137">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9dc91-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="9dc91-138">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9dc91-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9dc91-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="9dc91-140">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="9dc91-140">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
