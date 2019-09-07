---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397525"
---
# <a name="workflowinstancemanagement"></a><span data-ttu-id="69f8c-101">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="69f8c-101">\<workflowInstanceManagement></span></span>
<span data-ttu-id="69f8c-102">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="69f8c-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
<span data-ttu-id="69f8c-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="69f8c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="69f8c-104">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="69f8c-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="69f8c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="69f8c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="69f8c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="69f8c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="69f8c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="69f8c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="69f8c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceManagement >**</span><span class="sxs-lookup"><span data-stu-id="69f8c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f8c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69f8c-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69f8c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="69f8c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="69f8c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="69f8c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69f8c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="69f8c-112">Attributes</span></span>  
  
|<span data-ttu-id="69f8c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="69f8c-113">Attribute</span></span>|<span data-ttu-id="69f8c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="69f8c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69f8c-115">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="69f8c-115">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="69f8c-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="69f8c-116">Child Elements</span></span>  
 <span data-ttu-id="69f8c-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="69f8c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69f8c-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="69f8c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="69f8c-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="69f8c-119">Element</span></span>|<span data-ttu-id="69f8c-120">Popis</span><span class="sxs-lookup"><span data-stu-id="69f8c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69f8c-121">\<chování > \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="69f8c-121">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="69f8c-122">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="69f8c-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="69f8c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69f8c-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
