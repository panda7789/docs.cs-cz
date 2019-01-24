---
title: '&lt;Služba&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: e91e04c602fd867e329477015fc0a8354ae26a05
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535005"
---
# <a name="ltservicegt"></a><span data-ttu-id="59d6c-102">&lt;Služba&gt;</span><span class="sxs-lookup"><span data-stu-id="59d6c-102">&lt;service&gt;</span></span>
<span data-ttu-id="59d6c-103">`service` Element obsahuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="59d6c-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="59d6c-104">Obsahuje také koncové body, které zpřístupňují služby.</span><span class="sxs-lookup"><span data-stu-id="59d6c-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="59d6c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="59d6c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="59d6c-106">\<services></span><span class="sxs-lookup"><span data-stu-id="59d6c-106">\<services></span></span>  
<span data-ttu-id="59d6c-107">\<služby ></span><span class="sxs-lookup"><span data-stu-id="59d6c-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d6c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59d6c-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59d6c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59d6c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="59d6c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59d6c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59d6c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="59d6c-111">Attributes</span></span>  
  
|<span data-ttu-id="59d6c-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="59d6c-112">Attribute</span></span>|<span data-ttu-id="59d6c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="59d6c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59d6c-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="59d6c-114">behaviorConfiguration</span></span>|<span data-ttu-id="59d6c-115">Řetězec obsahující název chování, jenž bude použit k vytvoření instance služby.</span><span class="sxs-lookup"><span data-stu-id="59d6c-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="59d6c-116">Název musí být v rozsahu od bodu služby je definována.</span><span class="sxs-lookup"><span data-stu-id="59d6c-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="59d6c-117">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="59d6c-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="59d6c-118">name</span><span class="sxs-lookup"><span data-stu-id="59d6c-118">name</span></span>|<span data-ttu-id="59d6c-119">Požadovaný atribut typu řetězec, který určuje typ služby, který má být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="59d6c-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="59d6c-120">Toto nastavení musí odpovídá platného typu.</span><span class="sxs-lookup"><span data-stu-id="59d6c-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="59d6c-121">By měl být ve formátu `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="59d6c-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59d6c-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59d6c-122">Child Elements</span></span>  
  
|<span data-ttu-id="59d6c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="59d6c-123">Element</span></span>|<span data-ttu-id="59d6c-124">Popis</span><span class="sxs-lookup"><span data-stu-id="59d6c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59d6c-125">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="59d6c-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="59d6c-126">Kolekce `endpoint` prvky, které zpřístupňují této služby.</span><span class="sxs-lookup"><span data-stu-id="59d6c-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="59d6c-127">\<host></span><span class="sxs-lookup"><span data-stu-id="59d6c-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="59d6c-128">Určuje řadu tato instance služby.</span><span class="sxs-lookup"><span data-stu-id="59d6c-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="59d6c-129">Tento prvek je typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="59d6c-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59d6c-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59d6c-130">Parent Elements</span></span>  
  
|<span data-ttu-id="59d6c-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="59d6c-131">Element</span></span>|<span data-ttu-id="59d6c-132">Popis</span><span class="sxs-lookup"><span data-stu-id="59d6c-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59d6c-133">\<services></span><span class="sxs-lookup"><span data-stu-id="59d6c-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="59d6c-134">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="59d6c-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59d6c-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59d6c-135">Remarks</span></span>  
 <span data-ttu-id="59d6c-136">Služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="59d6c-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="59d6c-137">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="59d6c-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="59d6c-138">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="59d6c-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="59d6c-139">V této části a její obsah definování kontraktu služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="59d6c-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="59d6c-140">`behaviorConfiguration` Element je volitelné.</span><span class="sxs-lookup"><span data-stu-id="59d6c-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="59d6c-141">Určuje chování služba používá.</span><span class="sxs-lookup"><span data-stu-id="59d6c-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="59d6c-142">Chování určené v tomto atributu propojit chování v oboru ve stejném souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="59d6c-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="59d6c-143">Každá služba zpřístupňuje jeden nebo více koncových bodů, který má svou vlastní adresu a vazbu.</span><span class="sxs-lookup"><span data-stu-id="59d6c-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="59d6c-144">Všechny vazby používá v konfiguračním souboru musí být definován v rozsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="59d6c-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="59d6c-145">Vazby jsou propojeny do koncových bodů prostřednictvím kombinace atributů `name` a `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="59d6c-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="59d6c-146">`name` Atribut popisuje část vazby je definováno v.</span><span class="sxs-lookup"><span data-stu-id="59d6c-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="59d6c-147">`bindingConfiguration` Atribut definuje, která konfigurace bude v rámci oddílu vazby se používá.</span><span class="sxs-lookup"><span data-stu-id="59d6c-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="59d6c-148">Část vazby můžete definovat několik konfigurací.</span><span class="sxs-lookup"><span data-stu-id="59d6c-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59d6c-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="59d6c-149">Example</span></span>  
 <span data-ttu-id="59d6c-150">Toto je příklad konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="59d6c-150">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59d6c-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59d6c-151">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="59d6c-152">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="59d6c-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
