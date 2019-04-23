---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 108c349a44ed3ac902652f86241c1e96a622549b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204234"
---
# <a name="behaviors"></a><span data-ttu-id="f912e-101">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f912e-101">\<behaviors></span></span>
<span data-ttu-id="f912e-102">Tento prvek definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="f912e-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="f912e-103">Každou kolekci definuje chování elementů používané koncové body a služby.</span><span class="sxs-lookup"><span data-stu-id="f912e-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="f912e-104">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="f912e-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="f912e-105">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="f912e-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f912e-106">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f912e-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="f912e-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f912e-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f912e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f912e-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f912e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f912e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f912e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f912e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f912e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f912e-111">Attributes</span></span>  
 <span data-ttu-id="f912e-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="f912e-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f912e-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f912e-113">Child Elements</span></span>  
  
|<span data-ttu-id="f912e-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="f912e-114">Element</span></span>|<span data-ttu-id="f912e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f912e-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f912e-116">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f912e-116">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="f912e-117">Tento konfigurační oddíl představuje všechna chování definovaná pro určitý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f912e-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="f912e-118">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f912e-118">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="f912e-119">Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="f912e-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f912e-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f912e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f912e-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f912e-121">Element</span></span>|<span data-ttu-id="f912e-122">Popis</span><span class="sxs-lookup"><span data-stu-id="f912e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f912e-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f912e-123">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="f912e-124">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f912e-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f912e-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f912e-125">Remarks</span></span>  
 <span data-ttu-id="f912e-126">Můžete použít `<remove>` prvek, který chcete odebrat konkrétní chování z kolekce.</span><span class="sxs-lookup"><span data-stu-id="f912e-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="f912e-127">Uděláte to tak, stačí zadat název chování pro odebrání v `name` atribut `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f912e-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="f912e-128">Můžete také použít `<clear>` element – pomáhat zajistit, že kolekce chování začne tím, že zrušíte všechny obsah kolekce prázdný.</span><span class="sxs-lookup"><span data-stu-id="f912e-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f912e-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f912e-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="f912e-130">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="f912e-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="f912e-131">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="f912e-131">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="f912e-132">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="f912e-132">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="f912e-133">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="f912e-133">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="f912e-134">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f912e-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
