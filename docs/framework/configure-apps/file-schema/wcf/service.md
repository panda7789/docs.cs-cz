---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 57fbdd2cf7c398e611f835eeb4e924fb4f3e0c9e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270300"
---
# <a name="service"></a><span data-ttu-id="2434e-101">\<služby ></span><span class="sxs-lookup"><span data-stu-id="2434e-101">\<service></span></span>
<span data-ttu-id="2434e-102">`service` Element obsahuje nastavení pro službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2434e-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="2434e-103">Obsahuje také koncové body, které zpřístupňují služby.</span><span class="sxs-lookup"><span data-stu-id="2434e-103">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="2434e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2434e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2434e-105">\<services></span><span class="sxs-lookup"><span data-stu-id="2434e-105">\<services></span></span>  
<span data-ttu-id="2434e-106">\<služby ></span><span class="sxs-lookup"><span data-stu-id="2434e-106">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2434e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2434e-107">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2434e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2434e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2434e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2434e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2434e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2434e-110">Attributes</span></span>  
  
|<span data-ttu-id="2434e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2434e-111">Attribute</span></span>|<span data-ttu-id="2434e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2434e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2434e-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="2434e-113">behaviorConfiguration</span></span>|<span data-ttu-id="2434e-114">Řetězec obsahující název chování, jenž bude použit k vytvoření instance služby.</span><span class="sxs-lookup"><span data-stu-id="2434e-114">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="2434e-115">Název musí být v rozsahu od bodu služby je definována.</span><span class="sxs-lookup"><span data-stu-id="2434e-115">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="2434e-116">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2434e-116">The default value is an empty string.</span></span>|  
|<span data-ttu-id="2434e-117">name</span><span class="sxs-lookup"><span data-stu-id="2434e-117">name</span></span>|<span data-ttu-id="2434e-118">Požadovaný atribut typu řetězec, který určuje typ služby, který má být vytvořena.</span><span class="sxs-lookup"><span data-stu-id="2434e-118">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="2434e-119">Toto nastavení musí odpovídá platného typu.</span><span class="sxs-lookup"><span data-stu-id="2434e-119">This setting must equate to a valid type.</span></span> <span data-ttu-id="2434e-120">By měl být ve formátu `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="2434e-120">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2434e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2434e-121">Child Elements</span></span>  
  
|<span data-ttu-id="2434e-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="2434e-122">Element</span></span>|<span data-ttu-id="2434e-123">Popis</span><span class="sxs-lookup"><span data-stu-id="2434e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2434e-124">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="2434e-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="2434e-125">Kolekce `endpoint` prvky, které zpřístupňují této služby.</span><span class="sxs-lookup"><span data-stu-id="2434e-125">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="2434e-126">\<host></span><span class="sxs-lookup"><span data-stu-id="2434e-126">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="2434e-127">Určuje řadu tato instance služby.</span><span class="sxs-lookup"><span data-stu-id="2434e-127">Specifies the host of this service instance.</span></span> <span data-ttu-id="2434e-128">Tento prvek je typu <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="2434e-128">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2434e-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2434e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2434e-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="2434e-130">Element</span></span>|<span data-ttu-id="2434e-131">Popis</span><span class="sxs-lookup"><span data-stu-id="2434e-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2434e-132">\<services></span><span class="sxs-lookup"><span data-stu-id="2434e-132">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="2434e-133">Kořenový element všechny elementy konfigurace WCF.</span><span class="sxs-lookup"><span data-stu-id="2434e-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2434e-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2434e-134">Remarks</span></span>  
 <span data-ttu-id="2434e-135">Služby jsou definovány v `services` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="2434e-135">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="2434e-136">Sestavení může obsahovat libovolný počet služeb.</span><span class="sxs-lookup"><span data-stu-id="2434e-136">An assembly can contain any number of services.</span></span> <span data-ttu-id="2434e-137">Každá služba má svůj vlastní `service` konfigurační oddíl.</span><span class="sxs-lookup"><span data-stu-id="2434e-137">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="2434e-138">V této části a její obsah definování kontraktu služby, chování a koncové body konkrétní služby.</span><span class="sxs-lookup"><span data-stu-id="2434e-138">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="2434e-139">`behaviorConfiguration` Element je volitelné.</span><span class="sxs-lookup"><span data-stu-id="2434e-139">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="2434e-140">Určuje chování služba používá.</span><span class="sxs-lookup"><span data-stu-id="2434e-140">It identifies the behavior the service uses.</span></span> <span data-ttu-id="2434e-141">Chování určené v tomto atributu propojit chování v oboru ve stejném souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2434e-141">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="2434e-142">Každá služba zpřístupňuje jeden nebo více koncových bodů, který má svou vlastní adresu a vazbu.</span><span class="sxs-lookup"><span data-stu-id="2434e-142">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="2434e-143">Všechny vazby používá v konfiguračním souboru musí být definován v rozsahu souboru.</span><span class="sxs-lookup"><span data-stu-id="2434e-143">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="2434e-144">Vazby jsou propojeny do koncových bodů prostřednictvím kombinace atributů `name` a `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="2434e-144">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="2434e-145">`name` Atribut popisuje část vazby je definováno v.</span><span class="sxs-lookup"><span data-stu-id="2434e-145">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="2434e-146">`bindingConfiguration` Atribut definuje, která konfigurace bude v rámci oddílu vazby se používá.</span><span class="sxs-lookup"><span data-stu-id="2434e-146">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="2434e-147">Část vazby můžete definovat několik konfigurací.</span><span class="sxs-lookup"><span data-stu-id="2434e-147">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2434e-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="2434e-148">Example</span></span>  
 <span data-ttu-id="2434e-149">Toto je příklad konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="2434e-149">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2434e-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2434e-150">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="2434e-151">Konfigurace služeb</span><span class="sxs-lookup"><span data-stu-id="2434e-151">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
