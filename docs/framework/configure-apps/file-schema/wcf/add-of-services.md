---
title: <add> z <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: dc769097a3aede2522c1fa7a4cf8e36c2d8fdfe8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398294"
---
# <a name="add-of-services"></a><span data-ttu-id="e7ae4-102">\<add> z \<services></span><span class="sxs-lookup"><span data-stu-id="e7ae4-102">\<add> of \<services></span></span>
<span data-ttu-id="e7ae4-103">Určuje nastavení pro instanci <xref:System.Workflow.Runtime.WorkflowRuntime> pro hostování služeb Windows Communication Foundation založených na pracovních postupech (WCF).</span><span class="sxs-lookup"><span data-stu-id="e7ae4-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="e7ae4-104">Tento prvek je typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="e7ae4-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="e7ae4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7ae4-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7ae4-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e7ae4-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e7ae4-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7ae4-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="e7ae4-108">Attributes</span></span>  
  
|<span data-ttu-id="e7ae4-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="e7ae4-109">Attribute</span></span>|<span data-ttu-id="e7ae4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e7ae4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7ae4-111">typ</span><span class="sxs-lookup"><span data-stu-id="e7ae4-111">type</span></span>|<span data-ttu-id="e7ae4-112">Řetězec, který určuje název typu kvalifikovaného pro sestavení služby, která má být inicializována.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-112">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="e7ae4-113">Zadaná služba musí dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-113">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="e7ae4-114">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-114">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7ae4-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e7ae4-115">Child Elements</span></span>  
 <span data-ttu-id="e7ae4-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="e7ae4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7ae4-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e7ae4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e7ae4-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="e7ae4-118">Element</span></span>|<span data-ttu-id="e7ae4-119">Description</span><span class="sxs-lookup"><span data-stu-id="e7ae4-119">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services-of-workflowruntime.md)|<span data-ttu-id="e7ae4-120">Kolekce služeb, které budou přidány do <xref:System.Workflow.Runtime.WorkflowRuntime> modulu.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-120">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="e7ae4-121">Prvky jsou typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="e7ae4-121">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="e7ae4-122">Služby zadané v kolekci budou inicializovány modulem runtime pracovního postupu a přidány ke svým službám při <xref:System.Workflow.Runtime.WorkflowRuntime> volání příslušného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-122">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="e7ae4-123">Proto musí služby zadané v kolekci dodržovat určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-123">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="e7ae4-124">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-124">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7ae4-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7ae4-125">Remarks</span></span>  
 <span data-ttu-id="e7ae4-126">Služba zadaná v tomto elementu bude inicializována modulem runtime pracovního postupu a přidána ke svým službám při <xref:System.Workflow.Runtime.WorkflowRuntime> volání příslušného konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-126">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="e7ae4-127">Proto je nutné, aby Zadaná služba dodržovala určitá pravidla týkající se signatur jejich konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-127">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="e7ae4-128">Další informace naleznete v tématu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="e7ae4-128">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7ae4-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7ae4-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7ae4-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7ae4-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="e7ae4-131">[Konfigurační soubory pracovního postupu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e7ae4-131">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
