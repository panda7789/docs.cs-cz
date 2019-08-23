---
title: <endpoint> – element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 71ddb3b860870ee8feeeb36c3f64fa7bfebb0f10
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925816"
---
# <a name="endpoint-element"></a><span data-ttu-id="e6918-102">\<element > koncového bodu</span><span class="sxs-lookup"><span data-stu-id="e6918-102">\<endpoint> element</span></span>
<span data-ttu-id="e6918-103">Určuje vazbu, kontrakt a vlastnosti adresy koncového bodu služby, který slouží k vystavení služeb.</span><span class="sxs-lookup"><span data-stu-id="e6918-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="e6918-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6918-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6918-105">\<> služby</span><span class="sxs-lookup"><span data-stu-id="e6918-105">\<service></span></span>  
<span data-ttu-id="e6918-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="e6918-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6918-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6918-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6918-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e6918-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e6918-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e6918-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6918-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e6918-110">Attributes</span></span>  
  
|<span data-ttu-id="e6918-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e6918-111">Attribute</span></span>|<span data-ttu-id="e6918-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e6918-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6918-113">adresa</span><span class="sxs-lookup"><span data-stu-id="e6918-113">address</span></span>|<span data-ttu-id="e6918-114">Řetězec, který obsahuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e6918-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="e6918-115">Adresu lze zadat jako absolutní nebo relativní adresu.</span><span class="sxs-lookup"><span data-stu-id="e6918-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="e6918-116">Pokud je zadána relativní adresa, očekává se, že hostitel poskytne základní adresu vhodnou pro přenosové schéma používané ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="e6918-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="e6918-117">Pokud není adresa nakonfigurovaná, předpokládá se, že základní adresa je adresa pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e6918-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="e6918-118">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e6918-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="e6918-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e6918-119">behaviorConfiguration</span></span>|<span data-ttu-id="e6918-120">Řetězec obsahující název chování, které se má použít v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="e6918-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="e6918-121">vazba</span><span class="sxs-lookup"><span data-stu-id="e6918-121">binding</span></span>|<span data-ttu-id="e6918-122">Povinný atribut řetězce, který určuje typ vazby, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="e6918-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="e6918-123">Typ musí mít registrovaný konfigurační oddíl, aby na něj bylo odkazováno.</span><span class="sxs-lookup"><span data-stu-id="e6918-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="e6918-124">Typ je zaregistrován podle názvu oddílu, nikoli podle názvu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="e6918-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="e6918-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="e6918-125">bindingConfiguration</span></span>|<span data-ttu-id="e6918-126">Řetězec, který určuje název vazby vazby, která se má použít při vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e6918-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="e6918-127">Název vazby musí být v oboru v místě, kde je koncový bod definován.</span><span class="sxs-lookup"><span data-stu-id="e6918-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="e6918-128">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e6918-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="e6918-129">Tento atribut se používá ve spojení s `binding` pro odkazování na konkrétní konfiguraci vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="e6918-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="e6918-130">Nastavte tento atribut, pokud se pokoušíte použít vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="e6918-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="e6918-131">V opačném případě může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e6918-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="e6918-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="e6918-132">bindingName</span></span>|<span data-ttu-id="e6918-133">Řetězec, který určuje jedinečný kvalifikovaný název vazby pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="e6918-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="e6918-134">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e6918-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="e6918-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="e6918-135">bindingNamespace</span></span>|<span data-ttu-id="e6918-136">Řetězec, který určuje kvalifikovaný název oboru názvů vazby pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="e6918-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="e6918-137">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e6918-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="e6918-138">dodavatele</span><span class="sxs-lookup"><span data-stu-id="e6918-138">contract</span></span>|<span data-ttu-id="e6918-139">Řetězec označující kontrakt, který tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="e6918-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="e6918-140">Sestavení musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e6918-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="e6918-141">Pokud implementace služby implementuje jeden typ kontraktu, může být tato vlastnost vynechána.</span><span class="sxs-lookup"><span data-stu-id="e6918-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="e6918-142">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e6918-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="e6918-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="e6918-143">endpointConfiguration</span></span>|<span data-ttu-id="e6918-144">Řetězec, který určuje název standardního koncového bodu, který je nastaven `kind` atributem, který odkazuje na Další informace o konfiguraci tohoto standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e6918-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="e6918-145">V `<standardEndpoints>` části se musí definovat stejný název.</span><span class="sxs-lookup"><span data-stu-id="e6918-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="e6918-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="e6918-146">isSystemEndpoint</span></span>|<span data-ttu-id="e6918-147">Logická hodnota určující, zda je koncový bod koncovým bodem infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="e6918-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="e6918-148">plnění</span><span class="sxs-lookup"><span data-stu-id="e6918-148">kind</span></span>|<span data-ttu-id="e6918-149">Řetězec, který určuje typ použitého standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e6918-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="e6918-150">Typ musí být zaregistrován v `<extensions>` oddílu nebo v souboru Machine. config. Pokud není nic zadáno, vytvoří se běžný koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="e6918-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="e6918-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="e6918-151">listenUriMode</span></span>|<span data-ttu-id="e6918-152">Určuje, jak přenos zachází z `ListenUri` poskytované služby k naslouchání.</span><span class="sxs-lookup"><span data-stu-id="e6918-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="e6918-153">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="e6918-153">Valid values are</span></span><br /><br /> <span data-ttu-id="e6918-154">– Explicitní</span><span class="sxs-lookup"><span data-stu-id="e6918-154">-   Explicit</span></span><br /><span data-ttu-id="e6918-155">-Unique</span><span class="sxs-lookup"><span data-stu-id="e6918-155">-   Unique</span></span><br /><br /> <span data-ttu-id="e6918-156">Výchozí hodnota je explicitní.</span><span class="sxs-lookup"><span data-stu-id="e6918-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="e6918-157">listenUri</span><span class="sxs-lookup"><span data-stu-id="e6918-157">listenUri</span></span>|<span data-ttu-id="e6918-158">Řetězec určující identifikátor URI, na kterém naslouchá koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="e6918-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="e6918-159">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e6918-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="e6918-160">name</span><span class="sxs-lookup"><span data-stu-id="e6918-160">name</span></span>|<span data-ttu-id="e6918-161">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e6918-161">Optional attribute.</span></span> <span data-ttu-id="e6918-162">Řetězec, který určuje název koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="e6918-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="e6918-163">Výchozí hodnota je zřetězení názvu vazby a názvu popisu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e6918-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="e6918-164">Služby mohou mít několik koncových bodů, takže `name` atribut koncového bodu se liší od názvu služby.</span><span class="sxs-lookup"><span data-stu-id="e6918-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6918-165">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e6918-165">Child Elements</span></span>  
  
|<span data-ttu-id="e6918-166">Prvek</span><span class="sxs-lookup"><span data-stu-id="e6918-166">Element</span></span>|<span data-ttu-id="e6918-167">Popis</span><span class="sxs-lookup"><span data-stu-id="e6918-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6918-168">\<headers></span><span class="sxs-lookup"><span data-stu-id="e6918-168">\<headers></span></span>](headers.md)|<span data-ttu-id="e6918-169">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="e6918-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="e6918-170">\<identity></span><span class="sxs-lookup"><span data-stu-id="e6918-170">\<identity></span></span>](identity.md)|<span data-ttu-id="e6918-171">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="e6918-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6918-172">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e6918-172">Parent Elements</span></span>  
  
|<span data-ttu-id="e6918-173">Prvek</span><span class="sxs-lookup"><span data-stu-id="e6918-173">Element</span></span>|<span data-ttu-id="e6918-174">Popis</span><span class="sxs-lookup"><span data-stu-id="e6918-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6918-175">\<service></span><span class="sxs-lookup"><span data-stu-id="e6918-175">\<service></span></span>](service.md)|<span data-ttu-id="e6918-176">Konfigurační oddíl definující seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="e6918-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e6918-177">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6918-177">Example</span></span>  
 <span data-ttu-id="e6918-178">Toto je příklad konfigurace koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="e6918-178">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="e6918-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6918-179">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="e6918-180">Bod Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="e6918-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="e6918-181">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="e6918-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
