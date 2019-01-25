---
title: '&lt;workflowInstanceManagement&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: ba3d9415efc21012b470fd2e9a7f426ca8f3aad1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662059"
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="f770b-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="f770b-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="f770b-103">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="f770b-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="f770b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f770b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f770b-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f770b-105">\<behaviors></span></span>  
<span data-ttu-id="f770b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f770b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f770b-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f770b-107">\<behavior></span></span>  
<span data-ttu-id="f770b-108">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="f770b-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f770b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f770b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f770b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f770b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f770b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f770b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f770b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f770b-112">Attributes</span></span>  
  
|<span data-ttu-id="f770b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f770b-113">Attribute</span></span>|<span data-ttu-id="f770b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f770b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f770b-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="f770b-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="f770b-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f770b-116">Child Elements</span></span>  
 <span data-ttu-id="f770b-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="f770b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f770b-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f770b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f770b-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="f770b-119">Element</span></span>|<span data-ttu-id="f770b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f770b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f770b-121">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f770b-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="f770b-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="f770b-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f770b-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f770b-123">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
