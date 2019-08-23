---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: a22c72b7a683e3ecab4344c92e7d835a184a58d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947149"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="e9527-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="e9527-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="e9527-102">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="e9527-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="e9527-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e9527-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e9527-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e9527-104">\<behaviors></span></span>  
<span data-ttu-id="e9527-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e9527-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="e9527-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="e9527-106">\<behavior></span></span>  
<span data-ttu-id="e9527-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="e9527-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9527-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9527-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9527-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e9527-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e9527-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e9527-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9527-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e9527-111">Attributes</span></span>  
  
|<span data-ttu-id="e9527-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e9527-112">Attribute</span></span>|<span data-ttu-id="e9527-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e9527-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9527-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="e9527-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="e9527-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e9527-115">Child Elements</span></span>  
 <span data-ttu-id="e9527-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="e9527-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9527-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e9527-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e9527-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="e9527-118">Element</span></span>|<span data-ttu-id="e9527-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e9527-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9527-120">\<chování > \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e9527-120">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="e9527-121">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="e9527-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9527-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9527-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
