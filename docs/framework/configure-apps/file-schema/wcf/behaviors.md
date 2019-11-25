---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: bcdd26f038b343040d81b0add83bf166a5e3151f
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139690"
---
# <a name="behaviors"></a><span data-ttu-id="ff6e8-101">chování \<</span><span class="sxs-lookup"><span data-stu-id="ff6e8-101">\<behaviors></span></span>
<span data-ttu-id="ff6e8-102">Tento prvek definuje dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="ff6e8-103">Každá kolekce definuje prvky chování spotřebované koncovými body a službami v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="ff6e8-104">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="ff6e8-105">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ff6e8-106">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ff6e8-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
<span data-ttu-id="ff6e8-107">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ff6e8-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff6e8-108">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ff6e8-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ff6e8-109">&nbsp;&nbsp;&nbsp;&nbsp;**chování**\<</span><span class="sxs-lookup"><span data-stu-id="ff6e8-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff6e8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff6e8-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff6e8-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ff6e8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ff6e8-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff6e8-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="ff6e8-113">Attributes</span></span>  
 <span data-ttu-id="ff6e8-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="ff6e8-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ff6e8-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ff6e8-115">Child Elements</span></span>  
  
|<span data-ttu-id="ff6e8-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="ff6e8-116">Element</span></span>|<span data-ttu-id="ff6e8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ff6e8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff6e8-118">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ff6e8-118">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="ff6e8-119">Tento oddíl konfigurace představuje všechna chování definovaná pro konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-119">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="ff6e8-120">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ff6e8-120">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="ff6e8-121">Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-121">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff6e8-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ff6e8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ff6e8-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="ff6e8-123">Element</span></span>|<span data-ttu-id="ff6e8-124">Popis</span><span class="sxs-lookup"><span data-stu-id="ff6e8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff6e8-125">\<system. serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ff6e8-125">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="ff6e8-126">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ff6e8-126">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff6e8-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff6e8-127">Remarks</span></span>  
 <span data-ttu-id="ff6e8-128">Pomocí elementu `<remove>` můžete z kolekce odebrat konkrétní chování.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-128">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="ff6e8-129">Uděláte to tak, že jednoduše dodáte název chování, které se má odebrat, do atributu `name` `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-129">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="ff6e8-130">Můžete také použít `<clear>` element k ujištění, že kolekce chování je prázdná, vymazáním veškerého obsahu kolekce.</span><span class="sxs-lookup"><span data-stu-id="ff6e8-130">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6e8-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff6e8-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="ff6e8-132">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="ff6e8-132">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="ff6e8-133">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="ff6e8-133">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="ff6e8-134">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="ff6e8-134">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="ff6e8-135">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="ff6e8-135">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="ff6e8-136">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ff6e8-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
