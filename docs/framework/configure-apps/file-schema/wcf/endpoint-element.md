---
title: <endpoint>  – element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: 667086cda010daf51cb92116d636b9b526b4b34b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163407"
---
# <a name="endpoint-element"></a><span data-ttu-id="abb64-102">\<koncový bod > – element</span><span class="sxs-lookup"><span data-stu-id="abb64-102">\<endpoint> element</span></span>
<span data-ttu-id="abb64-103">Určuje vazbu, kontrakt a vlastnosti adresy koncového bodu služby, který se používá k vystavení služby.</span><span class="sxs-lookup"><span data-stu-id="abb64-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="abb64-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="abb64-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="abb64-105">\<služby ></span><span class="sxs-lookup"><span data-stu-id="abb64-105">\<service></span></span>  
<span data-ttu-id="abb64-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="abb64-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb64-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abb64-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abb64-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="abb64-108">Attributes and Elements</span></span>  
 <span data-ttu-id="abb64-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="abb64-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abb64-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="abb64-110">Attributes</span></span>  
  
|<span data-ttu-id="abb64-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="abb64-111">Attribute</span></span>|<span data-ttu-id="abb64-112">Popis</span><span class="sxs-lookup"><span data-stu-id="abb64-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="abb64-113">adresa</span><span class="sxs-lookup"><span data-stu-id="abb64-113">address</span></span>|<span data-ttu-id="abb64-114">Řetězec, který obsahuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="abb64-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="abb64-115">Adresa se dá nastavit jako absolutní nebo relativní adresu.</span><span class="sxs-lookup"><span data-stu-id="abb64-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="abb64-116">Pokud je zadána relativní adresa, hostitel se očekává poskytování vhodné pro schéma přenosu ve vazbě používá základní adresu.</span><span class="sxs-lookup"><span data-stu-id="abb64-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="abb64-117">Pokud není konfigurována adresa, základní adresa je považován za adresu pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="abb64-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="abb64-118">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="abb64-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="abb64-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="abb64-119">behaviorConfiguration</span></span>|<span data-ttu-id="abb64-120">Řetězec obsahující název chování pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="abb64-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="abb64-121">vazba</span><span class="sxs-lookup"><span data-stu-id="abb64-121">binding</span></span>|<span data-ttu-id="abb64-122">Požadovaný atribut typu řetězec, který určuje typ použité vazby.</span><span class="sxs-lookup"><span data-stu-id="abb64-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="abb64-123">Typ musí mít registrované konfigurační oddíl pro odkazovat.</span><span class="sxs-lookup"><span data-stu-id="abb64-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="abb64-124">Typ je zapsané podle názvu oddílu, nikoli podle názvu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="abb64-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="abb64-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="abb64-125">bindingConfiguration</span></span>|<span data-ttu-id="abb64-126">Řetězec určující název vazby, použita při vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="abb64-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="abb64-127">Název vazby musí být v rozsahu od bodu na koncový bod je definována.</span><span class="sxs-lookup"><span data-stu-id="abb64-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="abb64-128">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="abb64-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="abb64-129">Tento atribut se používá ve spojení s `binding` odkazovat konfigurace konkrétní vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="abb64-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="abb64-130">Tento atribut nastavte, pokud se pokoušíte použít vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="abb64-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="abb64-131">V opačném případě může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="abb64-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="abb64-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="abb64-132">bindingName</span></span>|<span data-ttu-id="abb64-133">Řetězec určující jedinečný kvalifikovaný název vazby pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="abb64-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="abb64-134">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="abb64-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="abb64-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="abb64-135">bindingNamespace</span></span>|<span data-ttu-id="abb64-136">Řetězec určující kvalifikovaný název oboru názvů vazby pro definice prostřednictvím WSDL exportu</span><span class="sxs-lookup"><span data-stu-id="abb64-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="abb64-137">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="abb64-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="abb64-138">kontrakt</span><span class="sxs-lookup"><span data-stu-id="abb64-138">contract</span></span>|<span data-ttu-id="abb64-139">Řetězec označující kontrakt, který tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="abb64-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="abb64-140">Sestavení musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="abb64-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="abb64-141">Pokud implementace služby implementuje typ jeden kontrakt, lze tuto vlastnost vynechat.</span><span class="sxs-lookup"><span data-stu-id="abb64-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="abb64-142">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="abb64-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="abb64-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="abb64-143">endpointConfiguration</span></span>|<span data-ttu-id="abb64-144">Řetězec určující název standardního koncového bodu, který je nastaven podle `kind` atribut, který odkazuje na další konfigurační informace tohoto standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="abb64-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="abb64-145">Se stejným názvem musí být definován v `<standardEndpoints>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="abb64-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="abb64-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="abb64-146">isSystemEndpoint</span></span>|<span data-ttu-id="abb64-147">Logická hodnota určující, zda je koncový bod koncovým bodem infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="abb64-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="abb64-148">Typ</span><span class="sxs-lookup"><span data-stu-id="abb64-148">kind</span></span>|<span data-ttu-id="abb64-149">Řetězec, který určuje typ standardně použitého koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="abb64-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="abb64-150">Typ musí být zaregistrovaný ve `<extensions>` části nebo v souboru machine.config. Pokud není zadáno žádné umístění, je vytvořen společný koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="abb64-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="abb64-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="abb64-151">listenUriMode</span></span>|<span data-ttu-id="abb64-152">Určuje, jak přenos zachází `ListenUri` poskytnutým službě k naslouchání.</span><span class="sxs-lookup"><span data-stu-id="abb64-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="abb64-153">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="abb64-153">Valid values are</span></span><br /><br /> <span data-ttu-id="abb64-154">-Explicitní</span><span class="sxs-lookup"><span data-stu-id="abb64-154">-   Explicit</span></span><br /><span data-ttu-id="abb64-155">-Jedinečné</span><span class="sxs-lookup"><span data-stu-id="abb64-155">-   Unique</span></span><br /><br /> <span data-ttu-id="abb64-156">Výchozí hodnota je explicitní.</span><span class="sxs-lookup"><span data-stu-id="abb64-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="abb64-157">listenUri</span><span class="sxs-lookup"><span data-stu-id="abb64-157">listenUri</span></span>|<span data-ttu-id="abb64-158">Řetězec určující identifikátor URI, na kterém naslouchá koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="abb64-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="abb64-159">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="abb64-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="abb64-160">name</span><span class="sxs-lookup"><span data-stu-id="abb64-160">name</span></span>|<span data-ttu-id="abb64-161">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="abb64-161">Optional attribute.</span></span> <span data-ttu-id="abb64-162">Řetězec určující název koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="abb64-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="abb64-163">Výchozí hodnota je zřetězení vazby název a popis název kontraktu.</span><span class="sxs-lookup"><span data-stu-id="abb64-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="abb64-164">Služby mohou mít několik koncových bodů, proto koncový bod `name` atributu se liší od názvu služby.</span><span class="sxs-lookup"><span data-stu-id="abb64-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abb64-165">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="abb64-165">Child Elements</span></span>  
  
|<span data-ttu-id="abb64-166">Prvek</span><span class="sxs-lookup"><span data-stu-id="abb64-166">Element</span></span>|<span data-ttu-id="abb64-167">Popis</span><span class="sxs-lookup"><span data-stu-id="abb64-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abb64-168">\<headers></span><span class="sxs-lookup"><span data-stu-id="abb64-168">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="abb64-169">Kolekce záhlaví adres.</span><span class="sxs-lookup"><span data-stu-id="abb64-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="abb64-170">\<identity></span><span class="sxs-lookup"><span data-stu-id="abb64-170">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="abb64-171">Identita, která umožňuje ověřování z koncového bodu jiné koncové body výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="abb64-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="abb64-172">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="abb64-172">Parent Elements</span></span>  
  
|<span data-ttu-id="abb64-173">Prvek</span><span class="sxs-lookup"><span data-stu-id="abb64-173">Element</span></span>|<span data-ttu-id="abb64-174">Popis</span><span class="sxs-lookup"><span data-stu-id="abb64-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="abb64-175">\<služby ></span><span class="sxs-lookup"><span data-stu-id="abb64-175">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="abb64-176">Konfigurační oddíl, který definuje seznam koncových bodů, které se klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="abb64-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="abb64-177">Příklad</span><span class="sxs-lookup"><span data-stu-id="abb64-177">Example</span></span>  
 <span data-ttu-id="abb64-178">Toto je příklad konfigurace koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="abb64-178">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="abb64-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abb64-179">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="abb64-180">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="abb64-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="abb64-181">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="abb64-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
