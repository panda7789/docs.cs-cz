---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: 108c349a44ed3ac902652f86241c1e96a622549b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701226"
---
# <a name="behaviors"></a><span data-ttu-id="00191-101">\<chování ></span><span class="sxs-lookup"><span data-stu-id="00191-101">\<behaviors></span></span>
<span data-ttu-id="00191-102">Tento prvek definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="00191-102">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="00191-103">Každou kolekci definuje chování elementů používané koncové body a služby.</span><span class="sxs-lookup"><span data-stu-id="00191-103">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="00191-104">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="00191-104">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="00191-105">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="00191-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="00191-106">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="00191-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="00191-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="00191-107">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00191-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00191-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00191-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="00191-109">Attributes and Elements</span></span>  
 <span data-ttu-id="00191-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="00191-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00191-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="00191-111">Attributes</span></span>  
 <span data-ttu-id="00191-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="00191-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="00191-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="00191-113">Child Elements</span></span>  
  
|<span data-ttu-id="00191-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="00191-114">Element</span></span>|<span data-ttu-id="00191-115">Popis</span><span class="sxs-lookup"><span data-stu-id="00191-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00191-116">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="00191-116">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="00191-117">Tento konfigurační oddíl představuje všechna chování definovaná pro určitý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="00191-117">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="00191-118">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="00191-118">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="00191-119">Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="00191-119">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00191-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="00191-120">Parent Elements</span></span>  
  
|<span data-ttu-id="00191-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="00191-121">Element</span></span>|<span data-ttu-id="00191-122">Popis</span><span class="sxs-lookup"><span data-stu-id="00191-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00191-123">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="00191-123">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="00191-124">Kořenový element všechny elementy konfigurace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="00191-124">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00191-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00191-125">Remarks</span></span>  
 <span data-ttu-id="00191-126">Můžete použít `<remove>` prvek, který chcete odebrat konkrétní chování z kolekce.</span><span class="sxs-lookup"><span data-stu-id="00191-126">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="00191-127">Uděláte to tak, stačí zadat název chování pro odebrání v `name` atribut `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="00191-127">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="00191-128">Můžete také použít `<clear>` element – pomáhat zajistit, že kolekce chování začne tím, že zrušíte všechny obsah kolekce prázdný.</span><span class="sxs-lookup"><span data-stu-id="00191-128">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00191-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00191-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="00191-130">Konfigurace a rozšíření modulu runtime pomocí chování</span><span class="sxs-lookup"><span data-stu-id="00191-130">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="00191-131">Konfigurace chování klienta</span><span class="sxs-lookup"><span data-stu-id="00191-131">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="00191-132">Nastavení chování klienta za běhu</span><span class="sxs-lookup"><span data-stu-id="00191-132">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="00191-133">Určování chování služby za běhu</span><span class="sxs-lookup"><span data-stu-id="00191-133">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="00191-134">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="00191-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
