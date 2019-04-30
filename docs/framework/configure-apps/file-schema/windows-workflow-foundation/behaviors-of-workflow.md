---
title: <behaviors> pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: b7c5cf93a82ac88c25f9c478ad52cf41eb6f6d65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790296"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="66919-102">\<chování > pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="66919-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="66919-103">Tento prvek obsahuje **serviceBehaviors** kolekce.</span><span class="sxs-lookup"><span data-stu-id="66919-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="66919-104">Každý prvek v kolekci definuje chování elementů používané služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="66919-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="66919-105">Každý prvek chování je identifikován jeho jedinečné **název** atribut.</span><span class="sxs-lookup"><span data-stu-id="66919-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="66919-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="66919-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66919-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66919-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66919-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="66919-108">Attributes and Elements</span></span>  
 <span data-ttu-id="66919-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="66919-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66919-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="66919-110">Attributes</span></span>  
 <span data-ttu-id="66919-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="66919-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66919-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="66919-112">Child Elements</span></span>  
  
|<span data-ttu-id="66919-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="66919-113">Element</span></span>|<span data-ttu-id="66919-114">Popis</span><span class="sxs-lookup"><span data-stu-id="66919-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66919-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="66919-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="66919-116">Tento oddíl konfigurace představuje všechny chování definované pro službu konkrétního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="66919-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66919-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="66919-117">Parent Elements</span></span>  
  
|<span data-ttu-id="66919-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="66919-118">Element</span></span>|<span data-ttu-id="66919-119">Popis</span><span class="sxs-lookup"><span data-stu-id="66919-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66919-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="66919-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="66919-121">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="66919-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66919-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66919-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="66919-123">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="66919-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
