---
title: '&lt;Služby&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 6e83e988920d24c6fe7615e40334919caf21652e
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2018
ms.locfileid: "34059027"
---
# <a name="ltservicegt"></a><span data-ttu-id="ccacf-102">&lt;Služby&gt;</span><span class="sxs-lookup"><span data-stu-id="ccacf-102">&lt;service&gt;</span></span>
<span data-ttu-id="ccacf-103">`service` Element obsahuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ccacf-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="ccacf-104">Obsahuje taky koncových bodů, které službu vystavit.</span><span class="sxs-lookup"><span data-stu-id="ccacf-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="ccacf-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ccacf-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccacf-106">\<služby ></span><span class="sxs-lookup"><span data-stu-id="ccacf-106">\<services></span></span>  
<span data-ttu-id="ccacf-107">\<služby ></span><span class="sxs-lookup"><span data-stu-id="ccacf-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccacf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccacf-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration=String"  
        name="String">  
</service>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccacf-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ccacf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ccacf-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ccacf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccacf-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ccacf-111">Attributes</span></span>  
  
|<span data-ttu-id="ccacf-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ccacf-112">Attribute</span></span>|<span data-ttu-id="ccacf-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ccacf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ccacf-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ccacf-114">behaviorConfiguration</span></span>|<span data-ttu-id="ccacf-115">Řetězec, který obsahuje název chování chování, který se má použít k vytvoření instance služby.</span><span class="sxs-lookup"><span data-stu-id="ccacf-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="ccacf-116">Název chování musí být v rozsahu na bod, který je definován službu.</span><span class="sxs-lookup"><span data-stu-id="ccacf-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="ccacf-117">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ccacf-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="ccacf-118">name</span><span class="sxs-lookup"><span data-stu-id="ccacf-118">name</span></span>|<span data-ttu-id="ccacf-119">Vyžaduje atribut řetězec, který určuje typ službu, kterou chcete vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="ccacf-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="ccacf-120">Toto nastavení musí rovnat platného typu.</span><span class="sxs-lookup"><span data-stu-id="ccacf-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="ccacf-121">Musí být ve formátu `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="ccacf-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccacf-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ccacf-122">Child Elements</span></span>  
  
|<span data-ttu-id="ccacf-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="ccacf-123">Element</span></span>|<span data-ttu-id="ccacf-124">Popis</span><span class="sxs-lookup"><span data-stu-id="ccacf-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccacf-125">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="ccacf-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="ccacf-126">Kolekce `endpoint` elementy, které zveřejňují této služby.</span><span class="sxs-lookup"><span data-stu-id="ccacf-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="ccacf-127">\<hostitele ></span><span class="sxs-lookup"><span data-stu-id="ccacf-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="ccacf-128">Určuje hostitele této instance služby.</span><span class="sxs-lookup"><span data-stu-id="ccacf-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="ccacf-129">Tento element je typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="ccacf-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ccacf-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ccacf-130">Parent Elements</span></span>  
  
|<span data-ttu-id="ccacf-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="ccacf-131">Element</span></span>|<span data-ttu-id="ccacf-132">Popis</span><span class="sxs-lookup"><span data-stu-id="ccacf-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccacf-133">\<služby ></span><span class="sxs-lookup"><span data-stu-id="ccacf-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="ccacf-134">Kořenový element všechny konfigurační prvky WCF.</span><span class="sxs-lookup"><span data-stu-id="ccacf-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccacf-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccacf-135">Remarks</span></span>  
 <span data-ttu-id="ccacf-136">Služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="ccacf-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="ccacf-137">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="ccacf-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="ccacf-138">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="ccacf-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="ccacf-139">V této části a jejího obsahu definovat kontrakt služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="ccacf-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="ccacf-140">`behaviorConfiguration` Prvek je volitelný.</span><span class="sxs-lookup"><span data-stu-id="ccacf-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="ccacf-141">Určuje chování služba používá.</span><span class="sxs-lookup"><span data-stu-id="ccacf-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="ccacf-142">Chování v tomto atributu musí propojit chování v oboru ve stejném souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ccacf-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="ccacf-143">Každá služba zpřístupní jeden nebo více koncových bodů, které má svou vlastní adresu a vazby.</span><span class="sxs-lookup"><span data-stu-id="ccacf-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="ccacf-144">Všechny vazby používaných v rámci konfiguračního souboru musí být definován v oboru souboru.</span><span class="sxs-lookup"><span data-stu-id="ccacf-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="ccacf-145">Vazba jsou propojeny s koncových bodů prostřednictvím kombinace atributů `name` a `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="ccacf-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="ccacf-146">`name` Atribut popisuje části vazba je definováno v.</span><span class="sxs-lookup"><span data-stu-id="ccacf-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="ccacf-147">`bindingConfiguration` Atribut definuje, jakou konfiguraci v oddílu vazby se používá.</span><span class="sxs-lookup"><span data-stu-id="ccacf-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="ccacf-148">Vazba části můžete definovat několik konfigurací.</span><span class="sxs-lookup"><span data-stu-id="ccacf-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccacf-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccacf-149">Example</span></span>  
 <span data-ttu-id="ccacf-150">Toto je příklad konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="ccacf-150">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccacf-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccacf-151">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [<span data-ttu-id="ccacf-152">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="ccacf-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
