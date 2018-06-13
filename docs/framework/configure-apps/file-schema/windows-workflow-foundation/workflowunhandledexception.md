---
title: '&lt;workflowUnhandledException&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: d9db6ecc2e95e0d1ec5738f1d2f4a09a89c57f21
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755133"
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="4f264-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="4f264-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="4f264-103">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="4f264-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="4f264-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4f264-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4f264-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4f264-105">\<behaviors></span></span>  
<span data-ttu-id="4f264-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4f264-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4f264-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="4f264-107">\<behavior></span></span>  
<span data-ttu-id="4f264-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="4f264-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f264-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f264-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f264-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4f264-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4f264-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4f264-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f264-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4f264-112">Attributes</span></span>  
  
|<span data-ttu-id="4f264-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4f264-113">Attribute</span></span>|<span data-ttu-id="4f264-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4f264-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f264-115">Akce</span><span class="sxs-lookup"><span data-stu-id="4f264-115">action</span></span>|<span data-ttu-id="4f264-116">Řetězec, který určuje akci, která se má provést, když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="4f264-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="4f264-117">Tento atribut je typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="4f264-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f264-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4f264-118">Child Elements</span></span>  
 <span data-ttu-id="4f264-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="4f264-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f264-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4f264-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4f264-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="4f264-121">Element</span></span>|<span data-ttu-id="4f264-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4f264-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f264-123">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4f264-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="4f264-124">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="4f264-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f264-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f264-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
