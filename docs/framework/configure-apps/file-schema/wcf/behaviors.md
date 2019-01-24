---
title: '&lt;Chování&gt;'
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: a6786efb289ee66da3f0635e1a86e23f9b7302d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528430"
---
# <a name="ltbehaviorsgt"></a><span data-ttu-id="7897b-102">&lt;Chování&gt;</span><span class="sxs-lookup"><span data-stu-id="7897b-102">&lt;behaviors&gt;</span></span>
<span data-ttu-id="7897b-103">Tento prvek definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="7897b-103">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="7897b-104">Každou kolekci definuje chování elementů používané koncové body a služby.</span><span class="sxs-lookup"><span data-stu-id="7897b-104">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="7897b-105">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="7897b-105">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="7897b-106">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="7897b-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7897b-107">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7897b-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="7897b-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7897b-108">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7897b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7897b-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7897b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7897b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7897b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7897b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7897b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7897b-112">Attributes</span></span>  
 <span data-ttu-id="7897b-113">Žádná</span><span class="sxs-lookup"><span data-stu-id="7897b-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7897b-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7897b-114">Child Elements</span></span>  
  
|<span data-ttu-id="7897b-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="7897b-115">Element</span></span>|<span data-ttu-id="7897b-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7897b-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7897b-117">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7897b-117">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="7897b-118">Tento konfigurační oddíl představuje všechna chování definovaná pro určitý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7897b-118">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="7897b-119">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7897b-119">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="7897b-120">Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="7897b-120">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7897b-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7897b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7897b-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="7897b-122">Element</span></span>|<span data-ttu-id="7897b-123">Popis</span><span class="sxs-lookup"><span data-stu-id="7897b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7897b-124">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7897b-124">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="7897b-125">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7897b-125">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7897b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7897b-126">Remarks</span></span>  
 <span data-ttu-id="7897b-127">Můžete použít `<remove>` prvek, který chcete odebrat konkrétní chování z kolekce.</span><span class="sxs-lookup"><span data-stu-id="7897b-127">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="7897b-128">Uděláte to tak, stačí zadat název chování pro odebrání v `name` atribut `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7897b-128">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="7897b-129">Můžete také použít `<clear>` element – pomáhat zajistit, že kolekce chování začne tím, že zrušíte všechny obsah kolekce prázdný.</span><span class="sxs-lookup"><span data-stu-id="7897b-129">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7897b-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7897b-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="7897b-131">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="7897b-131">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="7897b-132">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="7897b-132">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="7897b-133">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="7897b-133">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="7897b-134">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="7897b-134">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="7897b-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7897b-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
