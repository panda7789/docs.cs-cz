---
title: <behaviors>pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 7dd3b0b20c9d7accd80a85b3693e67ffc9b729e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945992"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="e8bc9-102">\<chování > pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="e8bc9-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="e8bc9-103">Tento prvek obsahuje kolekci **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="e8bc9-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="e8bc9-104">Každý prvek v kolekci definuje chování elementů používané služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e8bc9-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="e8bc9-105">Každý prvek chování je identifikován podle jeho jedinečného atributu **Name** .</span><span class="sxs-lookup"><span data-stu-id="e8bc9-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="e8bc9-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e8bc9-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8bc9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8bc9-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8bc9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e8bc9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e8bc9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e8bc9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8bc9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e8bc9-110">Attributes</span></span>  
 <span data-ttu-id="e8bc9-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="e8bc9-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8bc9-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e8bc9-112">Child Elements</span></span>  
  
|<span data-ttu-id="e8bc9-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8bc9-113">Element</span></span>|<span data-ttu-id="e8bc9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e8bc9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8bc9-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e8bc9-115">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="e8bc9-116">Tento oddíl konfigurace představuje všechny chování definované pro službu konkrétního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e8bc9-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8bc9-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e8bc9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e8bc9-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8bc9-118">Element</span></span>|<span data-ttu-id="e8bc9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e8bc9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8bc9-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e8bc9-120">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="e8bc9-121">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e8bc9-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8bc9-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8bc9-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="e8bc9-123">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="e8bc9-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
