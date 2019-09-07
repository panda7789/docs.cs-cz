---
title: <behaviors>pracovního postupu
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398880"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="74367-102">\<chování > pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="74367-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="74367-103">Tento prvek obsahuje kolekci **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="74367-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="74367-104">Každý prvek v kolekci definuje chování elementů používané služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="74367-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="74367-105">Každý prvek chování je identifikován podle jeho jedinečného atributu **Name** .</span><span class="sxs-lookup"><span data-stu-id="74367-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
<span data-ttu-id="74367-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="74367-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="74367-107">&nbsp;&nbsp;[ **\<souborů. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="74367-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="74367-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<> chování**</span><span class="sxs-lookup"><span data-stu-id="74367-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74367-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74367-109">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74367-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74367-110">Attributes and Elements</span></span>  
 <span data-ttu-id="74367-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74367-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74367-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="74367-112">Attributes</span></span>  
 <span data-ttu-id="74367-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="74367-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="74367-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74367-114">Child Elements</span></span>  
  
|<span data-ttu-id="74367-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="74367-115">Element</span></span>|<span data-ttu-id="74367-116">Popis</span><span class="sxs-lookup"><span data-stu-id="74367-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74367-117">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="74367-117">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="74367-118">Tento oddíl konfigurace představuje všechny chování definované pro službu konkrétního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="74367-118">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74367-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74367-119">Parent Elements</span></span>  
  
|<span data-ttu-id="74367-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="74367-120">Element</span></span>|<span data-ttu-id="74367-121">Popis</span><span class="sxs-lookup"><span data-stu-id="74367-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74367-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="74367-122">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="74367-123">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="74367-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74367-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74367-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="74367-125">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="74367-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
