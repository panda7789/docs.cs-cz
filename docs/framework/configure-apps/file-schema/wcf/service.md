---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 69f3c70514fc2bcab1b4ef6a45036de98d1af7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936515"
---
# <a name="service"></a><span data-ttu-id="a89c9-101">\<> služby</span><span class="sxs-lookup"><span data-stu-id="a89c9-101">\<service></span></span>
<span data-ttu-id="a89c9-102">`service` Element obsahuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a89c9-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="a89c9-103">Obsahuje také koncové body, které zpřístupňují službu.</span><span class="sxs-lookup"><span data-stu-id="a89c9-103">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="a89c9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a89c9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a89c9-105">\<> služeb</span><span class="sxs-lookup"><span data-stu-id="a89c9-105">\<services></span></span>  
<span data-ttu-id="a89c9-106">\<> služby</span><span class="sxs-lookup"><span data-stu-id="a89c9-106">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a89c9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a89c9-107">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a89c9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a89c9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a89c9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a89c9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a89c9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a89c9-110">Attributes</span></span>  
  
|<span data-ttu-id="a89c9-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a89c9-111">Attribute</span></span>|<span data-ttu-id="a89c9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a89c9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a89c9-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a89c9-113">behaviorConfiguration</span></span>|<span data-ttu-id="a89c9-114">Řetězec obsahující název chování, který se má použít k vytvoření instance služby.</span><span class="sxs-lookup"><span data-stu-id="a89c9-114">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="a89c9-115">Název chování musí být v oboru v místě, kde je služba definovaná.</span><span class="sxs-lookup"><span data-stu-id="a89c9-115">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="a89c9-116">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="a89c9-116">The default value is an empty string.</span></span>|  
|<span data-ttu-id="a89c9-117">name</span><span class="sxs-lookup"><span data-stu-id="a89c9-117">name</span></span>|<span data-ttu-id="a89c9-118">Požadovaný atribut typu řetězec určující typ služby, pro kterou má být vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="a89c9-118">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="a89c9-119">Toto nastavení musí být rovno platnému typu.</span><span class="sxs-lookup"><span data-stu-id="a89c9-119">This setting must equate to a valid type.</span></span> <span data-ttu-id="a89c9-120">Formát by měl být`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="a89c9-120">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a89c9-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a89c9-121">Child Elements</span></span>  
  
|<span data-ttu-id="a89c9-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="a89c9-122">Element</span></span>|<span data-ttu-id="a89c9-123">Popis</span><span class="sxs-lookup"><span data-stu-id="a89c9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a89c9-124">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="a89c9-124">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="a89c9-125">Kolekce `endpoint` prvků, které zpřístupňují tuto službu.</span><span class="sxs-lookup"><span data-stu-id="a89c9-125">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="a89c9-126">\<host></span><span class="sxs-lookup"><span data-stu-id="a89c9-126">\<host></span></span>](host.md)|<span data-ttu-id="a89c9-127">Určuje hostitele této instance služby.</span><span class="sxs-lookup"><span data-stu-id="a89c9-127">Specifies the host of this service instance.</span></span> <span data-ttu-id="a89c9-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="a89c9-128">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a89c9-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a89c9-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a89c9-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="a89c9-130">Element</span></span>|<span data-ttu-id="a89c9-131">Popis</span><span class="sxs-lookup"><span data-stu-id="a89c9-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a89c9-132">\<services></span><span class="sxs-lookup"><span data-stu-id="a89c9-132">\<services></span></span>](services.md)|<span data-ttu-id="a89c9-133">Kořenový element všech elementů konfigurace služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a89c9-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a89c9-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a89c9-134">Remarks</span></span>  
 <span data-ttu-id="a89c9-135">Služby jsou definovány v `services` části konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a89c9-135">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="a89c9-136">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="a89c9-136">An assembly can contain any number of services.</span></span> <span data-ttu-id="a89c9-137">Každá služba má vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="a89c9-137">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="a89c9-138">Tato část a její obsah definují kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="a89c9-138">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="a89c9-139">`behaviorConfiguration` Prvek je také volitelný.</span><span class="sxs-lookup"><span data-stu-id="a89c9-139">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="a89c9-140">Určuje chování, které služba používá.</span><span class="sxs-lookup"><span data-stu-id="a89c9-140">It identifies the behavior the service uses.</span></span> <span data-ttu-id="a89c9-141">Chování zadané v tomto atributu musí být propojeno s chováním v oboru ve stejném konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a89c9-141">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="a89c9-142">Každá služba zveřejňuje jeden nebo více koncových bodů, které mají svou vlastní adresu a vazbu.</span><span class="sxs-lookup"><span data-stu-id="a89c9-142">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="a89c9-143">Všechny vazby používané v konfiguračním souboru musí být definovány v rozsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="a89c9-143">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="a89c9-144">Vazba je propojena s koncovými body prostřednictvím kombinace atributů `name` a `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a89c9-144">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="a89c9-145">`name` Atribut popisuje oddíl, ve kterém je vazba definována.</span><span class="sxs-lookup"><span data-stu-id="a89c9-145">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="a89c9-146">`bindingConfiguration` Atribut určuje, která konfigurace v rámci vazby je použita.</span><span class="sxs-lookup"><span data-stu-id="a89c9-146">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="a89c9-147">Oddíl Binding může definovat několik konfigurací.</span><span class="sxs-lookup"><span data-stu-id="a89c9-147">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a89c9-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="a89c9-148">Example</span></span>  
 <span data-ttu-id="a89c9-149">Toto je příklad konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="a89c9-149">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a89c9-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a89c9-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="a89c9-151">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="a89c9-151">Configuring Services</span></span>](../../../wcf/configuring-services.md)
