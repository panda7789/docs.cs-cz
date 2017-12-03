---
title: "&lt;chování&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f543742ee4d70f64d3bef64be295a7f353c680d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorsgt"></a><span data-ttu-id="7f7c0-102">&lt;chování&gt;</span><span class="sxs-lookup"><span data-stu-id="7f7c0-102">&lt;behaviors&gt;</span></span>
<span data-ttu-id="7f7c0-103">Tento element definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-103">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="7f7c0-104">Každá kolekce definuje chování elementy spotřebovávají koncové body a služby.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-104">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="7f7c0-105">Každý prvek chování je identifikován jeho jedinečné `name` atributu.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-105">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="7f7c0-106">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7f7c0-107">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7f7c0-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="7f7c0-108">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7f7c0-108">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f7c0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f7c0-109">Syntax</span></span>  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
   <endpointBehaviors>  
   </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f7c0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7f7c0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f7c0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f7c0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7f7c0-112">Attributes</span></span>  
 <span data-ttu-id="7f7c0-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="7f7c0-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f7c0-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7f7c0-114">Child Elements</span></span>  
  
|<span data-ttu-id="7f7c0-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f7c0-115">Element</span></span>|<span data-ttu-id="7f7c0-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7f7c0-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f7c0-117">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7f7c0-117">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="7f7c0-118">Tento konfigurační oddíl představuje všechny chování definované pro konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-118">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="7f7c0-119">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7f7c0-119">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="7f7c0-120">Tento oddíl konfigurace představuje všechny chování, které jsou definovány pro konkrétní službu.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-120">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f7c0-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7f7c0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7f7c0-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="7f7c0-122">Element</span></span>|<span data-ttu-id="7f7c0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="7f7c0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f7c0-124">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7f7c0-124">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="7f7c0-125">Kořenový element všechny konfigurační prvky Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7f7c0-125">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f7c0-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f7c0-126">Remarks</span></span>  
 <span data-ttu-id="7f7c0-127">Můžete použít `<remove>` elementu, který chcete odstranit konkrétní chování z kolekce.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-127">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="7f7c0-128">Uděláte to tak, jednoduše zadejte název požadované chování, odeberte v `name` atribut `<remove>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-128">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="7f7c0-129">Můžete také `<clear>` element zajistit, že začne kolekci chování prázdný zrušením se veškerý obsah kolekce.</span><span class="sxs-lookup"><span data-stu-id="7f7c0-129">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f7c0-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f7c0-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="7f7c0-131">Konfigurace a rozšíření modulu Runtime s chováním</span><span class="sxs-lookup"><span data-stu-id="7f7c0-131">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 [<span data-ttu-id="7f7c0-132">Konfigurace chování klientů</span><span class="sxs-lookup"><span data-stu-id="7f7c0-132">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="7f7c0-133">Určení chování klienta</span><span class="sxs-lookup"><span data-stu-id="7f7c0-133">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="7f7c0-134">Určení chování služby</span><span class="sxs-lookup"><span data-stu-id="7f7c0-134">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)  
 [<span data-ttu-id="7f7c0-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7f7c0-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
