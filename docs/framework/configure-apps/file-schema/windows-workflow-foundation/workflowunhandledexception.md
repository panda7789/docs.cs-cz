---
title: '&lt;workflowUnhandledException&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4266eb6480c98c7ea1b96f2325a018b0fdcba041
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowunhandledexceptiongt"></a><span data-ttu-id="6f6dd-102">&lt;workflowUnhandledException&gt;</span><span class="sxs-lookup"><span data-stu-id="6f6dd-102">&lt;workflowUnhandledException&gt;</span></span>
<span data-ttu-id="6f6dd-103">Chování služby, který umožňuje určit akci, která má provést při dojde k neošetřené výjimce v rámci pracovního postupu služby.</span><span class="sxs-lookup"><span data-stu-id="6f6dd-103">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
<span data-ttu-id="6f6dd-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6f6dd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6f6dd-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6f6dd-105">\<behaviors></span></span>  
<span data-ttu-id="6f6dd-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6f6dd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6f6dd-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6f6dd-107">\<behavior></span></span>  
<span data-ttu-id="6f6dd-108">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="6f6dd-108">\<workflowUnhandledException></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f6dd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f6dd-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f6dd-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6f6dd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6f6dd-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6f6dd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f6dd-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="6f6dd-112">Attributes</span></span>  
  
|<span data-ttu-id="6f6dd-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="6f6dd-113">Attribute</span></span>|<span data-ttu-id="6f6dd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6f6dd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f6dd-115">Akce</span><span class="sxs-lookup"><span data-stu-id="6f6dd-115">action</span></span>|<span data-ttu-id="6f6dd-116">Řetězec, který určuje akci, která se má provést, když dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="6f6dd-116">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="6f6dd-117">Tento atribut je typu<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span><span class="sxs-lookup"><span data-stu-id="6f6dd-117">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f6dd-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6f6dd-118">Child Elements</span></span>  
 <span data-ttu-id="6f6dd-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="6f6dd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f6dd-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6f6dd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6f6dd-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="6f6dd-121">Element</span></span>|<span data-ttu-id="6f6dd-122">Popis</span><span class="sxs-lookup"><span data-stu-id="6f6dd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f6dd-123">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6f6dd-123">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="6f6dd-124">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="6f6dd-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f6dd-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f6dd-125">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
