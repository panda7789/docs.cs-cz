---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: c12f57d68de870123d92c8a101e2999c24bb988f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855016"
---
# \<service>
<span data-ttu-id="34e2d-101">`service`Element obsahuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="34e2d-101">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="34e2d-102">Obsahuje také koncové body, které zpřístupňují službu.</span><span class="sxs-lookup"><span data-stu-id="34e2d-102">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="34e2d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34e2d-103">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34e2d-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="34e2d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="34e2d-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="34e2d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34e2d-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="34e2d-106">Attributes</span></span>  
  
|<span data-ttu-id="34e2d-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="34e2d-107">Attribute</span></span>|<span data-ttu-id="34e2d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="34e2d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34e2d-109">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="34e2d-109">behaviorConfiguration</span></span>|<span data-ttu-id="34e2d-110">Řetězec obsahující název chování, který se má použít k vytvoření instance služby.</span><span class="sxs-lookup"><span data-stu-id="34e2d-110">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="34e2d-111">Název chování musí být v oboru v místě, kde je služba definovaná.</span><span class="sxs-lookup"><span data-stu-id="34e2d-111">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="34e2d-112">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="34e2d-112">The default value is an empty string.</span></span>|  
|<span data-ttu-id="34e2d-113">name</span><span class="sxs-lookup"><span data-stu-id="34e2d-113">name</span></span>|<span data-ttu-id="34e2d-114">Požadovaný atribut typu řetězec určující typ služby, pro kterou má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="34e2d-114">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="34e2d-115">Toto nastavení musí být rovno platnému typu.</span><span class="sxs-lookup"><span data-stu-id="34e2d-115">This setting must equate to a valid type.</span></span> <span data-ttu-id="34e2d-116">Formát by měl být`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="34e2d-116">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34e2d-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="34e2d-117">Child Elements</span></span>  
  
|<span data-ttu-id="34e2d-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="34e2d-118">Element</span></span>|<span data-ttu-id="34e2d-119">Description</span><span class="sxs-lookup"><span data-stu-id="34e2d-119">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="34e2d-120">Kolekce `endpoint` prvků, které zpřístupňují tuto službu.</span><span class="sxs-lookup"><span data-stu-id="34e2d-120">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="34e2d-121">Určuje hostitele této instance služby.</span><span class="sxs-lookup"><span data-stu-id="34e2d-121">Specifies the host of this service instance.</span></span> <span data-ttu-id="34e2d-122">Tento prvek je typu <xref:System.ServiceModel.Configuration.HostElement> .</span><span class="sxs-lookup"><span data-stu-id="34e2d-122">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34e2d-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="34e2d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="34e2d-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="34e2d-124">Element</span></span>|<span data-ttu-id="34e2d-125">Description</span><span class="sxs-lookup"><span data-stu-id="34e2d-125">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="34e2d-126">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="34e2d-126">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34e2d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34e2d-127">Remarks</span></span>  
 <span data-ttu-id="34e2d-128">Služby jsou definovány v `services` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="34e2d-128">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="34e2d-129">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="34e2d-129">An assembly can contain any number of services.</span></span> <span data-ttu-id="34e2d-130">Každá služba má vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="34e2d-130">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="34e2d-131">Tato část a její obsah definují kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="34e2d-131">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="34e2d-132">`behaviorConfiguration`Prvek je také volitelný.</span><span class="sxs-lookup"><span data-stu-id="34e2d-132">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="34e2d-133">Určuje chování, které služba používá.</span><span class="sxs-lookup"><span data-stu-id="34e2d-133">It identifies the behavior the service uses.</span></span> <span data-ttu-id="34e2d-134">Chování zadané v tomto atributu musí být propojeno s chováním v oboru ve stejném konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="34e2d-134">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="34e2d-135">Každá služba zveřejňuje jeden nebo více koncových bodů, které mají svou vlastní adresu a vazbu.</span><span class="sxs-lookup"><span data-stu-id="34e2d-135">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="34e2d-136">Všechny vazby používané v konfiguračním souboru musí být definovány v rozsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="34e2d-136">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="34e2d-137">Vazba je propojena s koncovými body prostřednictvím kombinace atributů `name` a `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="34e2d-137">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="34e2d-138">`name`Atribut popisuje oddíl, ve kterém je vazba definována.</span><span class="sxs-lookup"><span data-stu-id="34e2d-138">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="34e2d-139">`bindingConfiguration`Atribut určuje, která konfigurace v rámci vazby je použita.</span><span class="sxs-lookup"><span data-stu-id="34e2d-139">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="34e2d-140">Oddíl Binding může definovat několik konfigurací.</span><span class="sxs-lookup"><span data-stu-id="34e2d-140">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34e2d-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="34e2d-141">Example</span></span>  
 <span data-ttu-id="34e2d-142">Toto je příklad konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="34e2d-142">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a><span data-ttu-id="34e2d-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="34e2d-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="34e2d-144">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="34e2d-144">Configuring Services</span></span>](../../../wcf/configuring-services.md)
