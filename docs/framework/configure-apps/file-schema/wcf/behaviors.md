---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 8fcb5ac0c552d1ac2e849c95a5c0757d0c142f3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926395"
---
# <a name="behaviors"></a><span data-ttu-id="93cc1-101">\<> chování</span><span class="sxs-lookup"><span data-stu-id="93cc1-101">\<behaviors></span></span>
<span data-ttu-id="93cc1-102">Tento prvek definuje dvě podřízené kolekce s `endpointBehaviors` názvem `serviceBehaviors`a.</span><span class="sxs-lookup"><span data-stu-id="93cc1-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="93cc1-103">Každá kolekce definuje prvky chování spotřebované koncovými body a službami v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="93cc1-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="93cc1-104">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="93cc1-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="93cc1-105">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="93cc1-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="93cc1-106">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="93cc1-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="93cc1-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="93cc1-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93cc1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93cc1-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93cc1-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="93cc1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="93cc1-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="93cc1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93cc1-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="93cc1-111">Attributes</span></span>  
 <span data-ttu-id="93cc1-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="93cc1-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="93cc1-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="93cc1-113">Child Elements</span></span>  
  
|<span data-ttu-id="93cc1-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="93cc1-114">Element</span></span>|<span data-ttu-id="93cc1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="93cc1-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93cc1-116">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="93cc1-116">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="93cc1-117">Tento oddíl konfigurace představuje všechna chování definovaná pro konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="93cc1-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="93cc1-118">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="93cc1-118">\<serviceBehaviors></span></span>](servicebehaviors.md)|<span data-ttu-id="93cc1-119">Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="93cc1-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93cc1-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="93cc1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="93cc1-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="93cc1-121">Element</span></span>|<span data-ttu-id="93cc1-122">Popis</span><span class="sxs-lookup"><span data-stu-id="93cc1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93cc1-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="93cc1-123">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="93cc1-124">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="93cc1-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93cc1-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93cc1-125">Remarks</span></span>  
 <span data-ttu-id="93cc1-126">Pomocí `<remove>` elementu můžete z kolekce odebrat konkrétní chování.</span><span class="sxs-lookup"><span data-stu-id="93cc1-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="93cc1-127">Uděláte to tak, že jednoduše dodáte název chování, které se má odebrat `name` , v atributu `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="93cc1-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="93cc1-128">Můžete také použít `<clear>` element k ujištění, že kolekce chování začne být prázdná vymazáním veškerého obsahu kolekce.</span><span class="sxs-lookup"><span data-stu-id="93cc1-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93cc1-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93cc1-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="93cc1-130">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="93cc1-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="93cc1-131">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="93cc1-131">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="93cc1-132">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="93cc1-132">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="93cc1-133">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="93cc1-133">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="93cc1-134">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="93cc1-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
