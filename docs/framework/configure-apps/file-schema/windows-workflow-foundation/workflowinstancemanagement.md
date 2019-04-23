---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 98bc1b24da6e65a11a39d133057c1bb55b003a58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191611"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="821f4-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="821f4-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="821f4-102">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="821f4-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="821f4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="821f4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="821f4-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="821f4-104">\<behaviors></span></span>  
<span data-ttu-id="821f4-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="821f4-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="821f4-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="821f4-106">\<behavior></span></span>  
<span data-ttu-id="821f4-107">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="821f4-107">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="821f4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="821f4-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="821f4-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="821f4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="821f4-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="821f4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="821f4-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="821f4-111">Attributes</span></span>  
  
|<span data-ttu-id="821f4-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="821f4-112">Attribute</span></span>|<span data-ttu-id="821f4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="821f4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="821f4-114">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="821f4-114">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="821f4-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="821f4-115">Child Elements</span></span>  
 <span data-ttu-id="821f4-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="821f4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="821f4-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="821f4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="821f4-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="821f4-118">Element</span></span>|<span data-ttu-id="821f4-119">Popis</span><span class="sxs-lookup"><span data-stu-id="821f4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="821f4-120">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="821f4-120">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="821f4-121">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="821f4-121">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="821f4-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="821f4-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
