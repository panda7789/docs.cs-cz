---
title: "&lt;chování&gt; pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40278c0a3d99dd5c37df1d642b8a2e13e9f62633
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="afc16-102">&lt;chování&gt; pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="afc16-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="afc16-103">Tento prvek obsahuje **serviceBehaviors** kolekce.</span><span class="sxs-lookup"><span data-stu-id="afc16-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="afc16-104">Každý prvek v kolekci definuje chování elementů používané služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="afc16-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="afc16-105">Každý prvek chování je určený podle jeho jedinečné **název** atribut.</span><span class="sxs-lookup"><span data-stu-id="afc16-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="afc16-106">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="afc16-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afc16-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afc16-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afc16-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="afc16-108">Attributes and Elements</span></span>  
 <span data-ttu-id="afc16-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="afc16-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afc16-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="afc16-110">Attributes</span></span>  
 <span data-ttu-id="afc16-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="afc16-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afc16-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="afc16-112">Child Elements</span></span>  
  
|<span data-ttu-id="afc16-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="afc16-113">Element</span></span>|<span data-ttu-id="afc16-114">Popis</span><span class="sxs-lookup"><span data-stu-id="afc16-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afc16-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="afc16-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="afc16-116">Tento oddíl konfigurace představuje všechny chování definované pro službu konkrétního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="afc16-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afc16-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="afc16-117">Parent Elements</span></span>  
  
|<span data-ttu-id="afc16-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="afc16-118">Element</span></span>|<span data-ttu-id="afc16-119">Popis</span><span class="sxs-lookup"><span data-stu-id="afc16-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afc16-120">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="afc16-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="afc16-121">Kořenový element všechny elementy konfigurace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="afc16-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afc16-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="afc16-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="afc16-123">Konfigurace a rozšíření modulu Runtime s chováním</span><span class="sxs-lookup"><span data-stu-id="afc16-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
