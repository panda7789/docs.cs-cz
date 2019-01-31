---
title: <behaviors> pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: e61a2078c5989a3b100e77e6b2f753b0ee5dd934
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271783"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="5c050-102">\<chování > pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="5c050-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="5c050-103">Tento prvek obsahuje **serviceBehaviors** kolekce.</span><span class="sxs-lookup"><span data-stu-id="5c050-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="5c050-104">Každý prvek v kolekci definuje chování elementů používané služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5c050-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="5c050-105">Každý prvek chování je identifikován jeho jedinečné **název** atribut.</span><span class="sxs-lookup"><span data-stu-id="5c050-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="5c050-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5c050-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c050-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c050-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c050-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5c050-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5c050-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5c050-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c050-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5c050-110">Attributes</span></span>  
 <span data-ttu-id="5c050-111">Žádná</span><span class="sxs-lookup"><span data-stu-id="5c050-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5c050-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5c050-112">Child Elements</span></span>  
  
|<span data-ttu-id="5c050-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="5c050-113">Element</span></span>|<span data-ttu-id="5c050-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5c050-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c050-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5c050-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="5c050-116">Tento oddíl konfigurace představuje všechny chování definované pro službu konkrétního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5c050-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c050-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5c050-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5c050-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="5c050-118">Element</span></span>|<span data-ttu-id="5c050-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5c050-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c050-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5c050-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="5c050-121">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="5c050-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c050-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c050-122">See also</span></span>
- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="5c050-123">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="5c050-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
