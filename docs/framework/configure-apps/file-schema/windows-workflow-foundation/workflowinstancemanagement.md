---
title: '&lt;workflowInstanceManagement&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: d86b0f61c6741fa156e04da75a62853f459324d1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767099"
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="96b41-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="96b41-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="96b41-103">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="96b41-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="96b41-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="96b41-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="96b41-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="96b41-105">\<behaviors></span></span>  
<span data-ttu-id="96b41-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="96b41-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="96b41-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="96b41-107">\<behavior></span></span>  
<span data-ttu-id="96b41-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="96b41-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b41-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96b41-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96b41-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="96b41-110">Attributes and Elements</span></span>  
 <span data-ttu-id="96b41-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="96b41-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96b41-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="96b41-112">Attributes</span></span>  
  
|<span data-ttu-id="96b41-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="96b41-113">Attribute</span></span>|<span data-ttu-id="96b41-114">Popis</span><span class="sxs-lookup"><span data-stu-id="96b41-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96b41-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="96b41-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="96b41-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="96b41-116">Child Elements</span></span>  
 <span data-ttu-id="96b41-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="96b41-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96b41-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="96b41-118">Parent Elements</span></span>  
  
|<span data-ttu-id="96b41-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="96b41-119">Element</span></span>|<span data-ttu-id="96b41-120">Popis</span><span class="sxs-lookup"><span data-stu-id="96b41-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96b41-121">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="96b41-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="96b41-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="96b41-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96b41-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="96b41-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
