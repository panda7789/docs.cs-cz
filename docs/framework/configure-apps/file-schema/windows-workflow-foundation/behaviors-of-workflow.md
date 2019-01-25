---
title: '&lt;chování&gt; pracovního postupu'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: b4ad7fb54cc8a03f5dd698055da5a29e719775c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731670"
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="c65e5-102">&lt;chování&gt; pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="c65e5-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="c65e5-103">Tento prvek obsahuje **serviceBehaviors** kolekce.</span><span class="sxs-lookup"><span data-stu-id="c65e5-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="c65e5-104">Každý prvek v kolekci definuje chování elementů používané služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c65e5-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="c65e5-105">Každý prvek chování je identifikován jeho jedinečné **název** atribut.</span><span class="sxs-lookup"><span data-stu-id="c65e5-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="c65e5-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c65e5-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65e5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c65e5-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c65e5-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c65e5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c65e5-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c65e5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c65e5-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c65e5-110">Attributes</span></span>  
 <span data-ttu-id="c65e5-111">Žádná</span><span class="sxs-lookup"><span data-stu-id="c65e5-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c65e5-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c65e5-112">Child Elements</span></span>  
  
|<span data-ttu-id="c65e5-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="c65e5-113">Element</span></span>|<span data-ttu-id="c65e5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c65e5-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c65e5-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c65e5-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="c65e5-116">Tento oddíl konfigurace představuje všechny chování definované pro službu konkrétního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c65e5-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c65e5-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c65e5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c65e5-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="c65e5-118">Element</span></span>|<span data-ttu-id="c65e5-119">Popis</span><span class="sxs-lookup"><span data-stu-id="c65e5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c65e5-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c65e5-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="c65e5-121">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c65e5-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c65e5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c65e5-122">See also</span></span>
- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="c65e5-123">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="c65e5-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
