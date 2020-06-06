---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: bcdd26f038b343040d81b0add83bf166a5e3151f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139690"
---
# \<behaviors>
<span data-ttu-id="925a8-101">Tento prvek definuje dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="925a8-101">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="925a8-102">Každá kolekce definuje prvky chování spotřebované koncovými body a službami v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="925a8-102">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="925a8-103">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="925a8-103">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="925a8-104">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="925a8-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="925a8-105">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="925a8-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="925a8-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="925a8-106">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="925a8-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="925a8-107">Attributes and Elements</span></span>  
 <span data-ttu-id="925a8-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="925a8-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="925a8-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="925a8-109">Attributes</span></span>  
 <span data-ttu-id="925a8-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="925a8-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="925a8-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="925a8-111">Child Elements</span></span>  
  
|<span data-ttu-id="925a8-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="925a8-112">Element</span></span>|<span data-ttu-id="925a8-113">Description</span><span class="sxs-lookup"><span data-stu-id="925a8-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="925a8-114">Tento oddíl konfigurace představuje všechna chování definovaná pro konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="925a8-114">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="925a8-115">Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="925a8-115">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="925a8-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="925a8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="925a8-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="925a8-117">Element</span></span>|<span data-ttu-id="925a8-118">Description</span><span class="sxs-lookup"><span data-stu-id="925a8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="925a8-119">Kořenový element všech prvků konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="925a8-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="925a8-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="925a8-120">Remarks</span></span>  
 <span data-ttu-id="925a8-121">Pomocí `<remove>` elementu můžete z kolekce odebrat konkrétní chování.</span><span class="sxs-lookup"><span data-stu-id="925a8-121">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="925a8-122">Uděláte to tak, že jednoduše dodáte název chování, které se má odebrat, v `name` atributu `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="925a8-122">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="925a8-123">Můžete také použít `<clear>` element k ujištění, že kolekce chování začne být prázdná vymazáním veškerého obsahu kolekce.</span><span class="sxs-lookup"><span data-stu-id="925a8-123">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="925a8-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="925a8-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="925a8-125">Konfigurace a rozšíření modulu runtime s chováním</span><span class="sxs-lookup"><span data-stu-id="925a8-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="925a8-126">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="925a8-126">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="925a8-127">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="925a8-127">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="925a8-128">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="925a8-128">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="925a8-129">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="925a8-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
