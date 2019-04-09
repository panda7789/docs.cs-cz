---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 98bc1b24da6e65a11a39d133057c1bb55b003a58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191611"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="2fee9-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="2fee9-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="2fee9-102">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="2fee9-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="2fee9-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2fee9-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2fee9-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2fee9-104">\<behaviors></span></span>  
<span data-ttu-id="2fee9-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2fee9-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="2fee9-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2fee9-106">\<behavior></span></span>  
<span data-ttu-id="2fee9-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="2fee9-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fee9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fee9-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2fee9-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2fee9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2fee9-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2fee9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2fee9-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2fee9-111">Attributes</span></span>  
  
|<span data-ttu-id="2fee9-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2fee9-112">Attribute</span></span>|<span data-ttu-id="2fee9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2fee9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2fee9-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="2fee9-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="2fee9-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2fee9-115">Child Elements</span></span>  
 <span data-ttu-id="2fee9-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="2fee9-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2fee9-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2fee9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2fee9-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="2fee9-118">Element</span></span>|<span data-ttu-id="2fee9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="2fee9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2fee9-120">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2fee9-120">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="2fee9-121">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2fee9-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2fee9-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2fee9-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
