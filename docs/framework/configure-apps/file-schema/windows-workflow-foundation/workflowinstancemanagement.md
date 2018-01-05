---
title: '&lt;workflowInstanceManagement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3be696133bff5c1fc8858ab31093866ed05c98a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="f39d3-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="f39d3-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="f39d3-103">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="f39d3-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="f39d3-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f39d3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f39d3-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f39d3-105">\<behaviors></span></span>  
<span data-ttu-id="f39d3-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f39d3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f39d3-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f39d3-107">\<behavior></span></span>  
<span data-ttu-id="f39d3-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="f39d3-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f39d3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f39d3-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f39d3-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f39d3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f39d3-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f39d3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f39d3-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f39d3-112">Attributes</span></span>  
  
|<span data-ttu-id="f39d3-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f39d3-113">Attribute</span></span>|<span data-ttu-id="f39d3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f39d3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f39d3-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="f39d3-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="f39d3-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f39d3-116">Child Elements</span></span>  
 <span data-ttu-id="f39d3-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="f39d3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f39d3-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f39d3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f39d3-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f39d3-119">Element</span></span>|<span data-ttu-id="f39d3-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f39d3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f39d3-121">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f39d3-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f39d3-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="f39d3-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f39d3-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f39d3-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
