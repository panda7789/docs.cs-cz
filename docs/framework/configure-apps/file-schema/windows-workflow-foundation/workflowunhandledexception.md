---
title: '&lt;workflowUnhandledException&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: 5c5dddc6d126811d7fd1eaae2f85df1e42c1cd41
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700868"
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="ab02b-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="ab02b-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="ab02b-103">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="ab02b-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="ab02b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ab02b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ab02b-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ab02b-105">\<behaviors></span></span>  
<span data-ttu-id="ab02b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ab02b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ab02b-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="ab02b-107">\<behavior></span></span>  
<span data-ttu-id="ab02b-108">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="ab02b-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab02b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab02b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab02b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab02b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ab02b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ab02b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab02b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab02b-112">Attributes</span></span>  
  
|<span data-ttu-id="ab02b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="ab02b-113">Attribute</span></span>|<span data-ttu-id="ab02b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ab02b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab02b-115">Akce</span><span class="sxs-lookup"><span data-stu-id="ab02b-115">action</span></span>|<span data-ttu-id="ab02b-116">Řetězec, který určuje akci, která se má provést, když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="ab02b-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="ab02b-117">Tento atribut je typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="ab02b-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab02b-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab02b-118">Child Elements</span></span>  
 <span data-ttu-id="ab02b-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="ab02b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab02b-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab02b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ab02b-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab02b-121">Element</span></span>|<span data-ttu-id="ab02b-122">Popis</span><span class="sxs-lookup"><span data-stu-id="ab02b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab02b-123">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ab02b-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="ab02b-124">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="ab02b-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab02b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab02b-125">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
