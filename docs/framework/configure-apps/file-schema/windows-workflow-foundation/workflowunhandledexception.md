---
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: cfe3350ac42d1e0e837b79f25753f62dc2051dd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096248"
---
# <a name="workflowunhandledexception"></a><span data-ttu-id="5794a-101">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="5794a-101">\<workflowUnhandledException></span></span>
<span data-ttu-id="5794a-102">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="5794a-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="5794a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5794a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5794a-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5794a-104">\<behaviors></span></span>  
<span data-ttu-id="5794a-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5794a-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="5794a-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5794a-106">\<behavior></span></span>  
<span data-ttu-id="5794a-107">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="5794a-107">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5794a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5794a-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5794a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5794a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5794a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5794a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5794a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="5794a-111">Attributes</span></span>  
  
|<span data-ttu-id="5794a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="5794a-112">Attribute</span></span>|<span data-ttu-id="5794a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5794a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5794a-114">Akce</span><span class="sxs-lookup"><span data-stu-id="5794a-114">action</span></span>|<span data-ttu-id="5794a-115">Řetězec, který určuje akci, která se má provést, když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="5794a-115">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="5794a-116">Tento atribut je typu</span><span class="sxs-lookup"><span data-stu-id="5794a-116">This attribute is of type</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>|  
  
### <a name="child-elements"></a><span data-ttu-id="5794a-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5794a-117">Child Elements</span></span>  
 <span data-ttu-id="5794a-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="5794a-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5794a-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5794a-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5794a-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="5794a-120">Element</span></span>|<span data-ttu-id="5794a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="5794a-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5794a-122">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5794a-122">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="5794a-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="5794a-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5794a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5794a-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
