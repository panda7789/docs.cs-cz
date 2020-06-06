---
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: aa2edafd9adc0317ed0023ad46688025dcecad67
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397525"
---
# \<workflowInstanceManagement>
<span data-ttu-id="b765f-101">Chování služby, která vám umožní zadat nastavení, které určují, jak jsou spuštěny instance pracovních postupů, včetně stálost, neošetřené výjimky chování a nečinnosti chování.</span><span class="sxs-lookup"><span data-stu-id="b765f-101">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="b765f-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b765f-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b765f-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b765f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b765f-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b765f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b765f-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="b765f-105">Attributes</span></span>  
  
|<span data-ttu-id="b765f-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="b765f-106">Attribute</span></span>|<span data-ttu-id="b765f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b765f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b765f-108">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="b765f-108">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="b765f-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b765f-109">Child Elements</span></span>  
 <span data-ttu-id="b765f-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="b765f-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b765f-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b765f-111">Parent Elements</span></span>  
  
|<span data-ttu-id="b765f-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="b765f-112">Element</span></span>|<span data-ttu-id="b765f-113">Description</span><span class="sxs-lookup"><span data-stu-id="b765f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b765f-114">\<behavior>tohoto\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b765f-114">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b765f-115">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="b765f-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b765f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b765f-116">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
