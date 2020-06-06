---
title: <behaviors>pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398880"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="6ed33-102">\<behaviors>pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6ed33-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="6ed33-103">Tento prvek obsahuje kolekci **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="6ed33-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="6ed33-104">Každý prvek v kolekci definuje chování elementů používané služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6ed33-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="6ed33-105">Každý prvek chování je identifikován podle jeho jedinečného atributu **Name** .</span><span class="sxs-lookup"><span data-stu-id="6ed33-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="6ed33-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ed33-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ed33-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6ed33-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6ed33-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6ed33-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ed33-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="6ed33-109">Attributes</span></span>  
 <span data-ttu-id="6ed33-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="6ed33-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6ed33-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6ed33-111">Child Elements</span></span>  
  
|<span data-ttu-id="6ed33-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="6ed33-112">Element</span></span>|<span data-ttu-id="6ed33-113">Description</span><span class="sxs-lookup"><span data-stu-id="6ed33-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="6ed33-114">Tento oddíl konfigurace představuje všechny chování definované pro službu konkrétního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6ed33-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6ed33-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6ed33-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6ed33-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="6ed33-116">Element</span></span>|<span data-ttu-id="6ed33-117">Description</span><span class="sxs-lookup"><span data-stu-id="6ed33-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="6ed33-118">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6ed33-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6ed33-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ed33-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="6ed33-120">Konfigurace a rozšíření modulu runtime s chováním</span><span class="sxs-lookup"><span data-stu-id="6ed33-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
