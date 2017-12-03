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
ms.openlocfilehash: 28e0f2b0ed88ee73edb52a8c18346746beb34771
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowinstancemanagementgt"></a><span data-ttu-id="0f160-102">&lt;workflowInstanceManagement&gt;</span><span class="sxs-lookup"><span data-stu-id="0f160-102">&lt;workflowInstanceManagement&gt;</span></span>
<span data-ttu-id="0f160-103">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="0f160-103">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="0f160-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0f160-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0f160-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0f160-105">\<behaviors></span></span>  
<span data-ttu-id="0f160-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0f160-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="0f160-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0f160-107">\<behavior></span></span>  
<span data-ttu-id="0f160-108">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="0f160-108">\<workflowInstanceManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f160-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f160-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f160-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0f160-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0f160-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0f160-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f160-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0f160-112">Attributes</span></span>  
  
|<span data-ttu-id="0f160-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0f160-113">Attribute</span></span>|<span data-ttu-id="0f160-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0f160-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f160-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="0f160-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="0f160-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0f160-116">Child Elements</span></span>  
 <span data-ttu-id="0f160-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="0f160-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f160-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0f160-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0f160-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="0f160-119">Element</span></span>|<span data-ttu-id="0f160-120">Popis</span><span class="sxs-lookup"><span data-stu-id="0f160-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f160-121">\<chování > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0f160-121">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="0f160-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="0f160-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f160-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f160-123">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>  
 <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
