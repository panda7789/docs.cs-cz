---
title: <endpoint> – element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855390"
---
# <a name="endpoint-element"></a><span data-ttu-id="c0b24-102">\<element > koncového bodu</span><span class="sxs-lookup"><span data-stu-id="c0b24-102">\<endpoint> element</span></span>
<span data-ttu-id="c0b24-103">Určuje vazbu, kontrakt a vlastnosti adresy koncového bodu služby, který slouží k vystavení služeb.</span><span class="sxs-lookup"><span data-stu-id="c0b24-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
<span data-ttu-id="c0b24-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0b24-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0b24-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c0b24-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c0b24-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služeb**](services.md)</span><span class="sxs-lookup"><span data-stu-id="c0b24-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="c0b24-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> služby**](service.md)</span><span class="sxs-lookup"><span data-stu-id="c0b24-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="c0b24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> koncového bodu**</span><span class="sxs-lookup"><span data-stu-id="c0b24-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b24-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0b24-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0b24-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c0b24-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c0b24-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c0b24-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0b24-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0b24-112">Attributes</span></span>  
  
|<span data-ttu-id="c0b24-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c0b24-113">Attribute</span></span>|<span data-ttu-id="c0b24-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b24-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0b24-115">adresa</span><span class="sxs-lookup"><span data-stu-id="c0b24-115">address</span></span>|<span data-ttu-id="c0b24-116">Řetězec, který obsahuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0b24-116">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="c0b24-117">Adresu lze zadat jako absolutní nebo relativní adresu.</span><span class="sxs-lookup"><span data-stu-id="c0b24-117">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="c0b24-118">Pokud je zadána relativní adresa, očekává se, že hostitel poskytne základní adresu vhodnou pro přenosové schéma používané ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="c0b24-118">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="c0b24-119">Pokud není adresa nakonfigurovaná, předpokládá se, že základní adresa je adresa pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c0b24-119">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="c0b24-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0b24-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="c0b24-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="c0b24-121">behaviorConfiguration</span></span>|<span data-ttu-id="c0b24-122">Řetězec obsahující název chování, které se má použít v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="c0b24-122">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="c0b24-123">vazba</span><span class="sxs-lookup"><span data-stu-id="c0b24-123">binding</span></span>|<span data-ttu-id="c0b24-124">Povinný atribut řetězce, který určuje typ vazby, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="c0b24-124">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="c0b24-125">Typ musí mít registrovaný konfigurační oddíl, aby na něj bylo odkazováno.</span><span class="sxs-lookup"><span data-stu-id="c0b24-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="c0b24-126">Typ je zaregistrován podle názvu oddílu, nikoli podle názvu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="c0b24-126">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="c0b24-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c0b24-127">bindingConfiguration</span></span>|<span data-ttu-id="c0b24-128">Řetězec, který určuje název vazby vazby, která se má použít při vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0b24-128">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="c0b24-129">Název vazby musí být v oboru v místě, kde je koncový bod definován.</span><span class="sxs-lookup"><span data-stu-id="c0b24-129">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="c0b24-130">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0b24-130">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="c0b24-131">Tento atribut se používá ve spojení s `binding` pro odkazování na konkrétní konfiguraci vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c0b24-131">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="c0b24-132">Nastavte tento atribut, pokud se pokoušíte použít vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="c0b24-132">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="c0b24-133">V opačném případě může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c0b24-133">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="c0b24-134">bindingName</span><span class="sxs-lookup"><span data-stu-id="c0b24-134">bindingName</span></span>|<span data-ttu-id="c0b24-135">Řetězec, který určuje jedinečný kvalifikovaný název vazby pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="c0b24-135">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="c0b24-136">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0b24-136">The default is an empty string.</span></span>|  
|<span data-ttu-id="c0b24-137">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="c0b24-137">bindingNamespace</span></span>|<span data-ttu-id="c0b24-138">Řetězec, který určuje kvalifikovaný název oboru názvů vazby pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="c0b24-138">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="c0b24-139">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0b24-139">The default is an empty string.</span></span>|  
|<span data-ttu-id="c0b24-140">Dodavatele</span><span class="sxs-lookup"><span data-stu-id="c0b24-140">contract</span></span>|<span data-ttu-id="c0b24-141">Řetězec označující kontrakt, který tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="c0b24-141">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="c0b24-142">Sestavení musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c0b24-142">The assembly must implement the contract type.</span></span> <span data-ttu-id="c0b24-143">Pokud implementace služby implementuje jeden typ kontraktu, může být tato vlastnost vynechána.</span><span class="sxs-lookup"><span data-stu-id="c0b24-143">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="c0b24-144">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0b24-144">The default is an empty string.</span></span>|  
|<span data-ttu-id="c0b24-145">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="c0b24-145">endpointConfiguration</span></span>|<span data-ttu-id="c0b24-146">Řetězec, který určuje název standardního koncového bodu, který je nastaven `kind` atributem, který odkazuje na Další informace o konfiguraci tohoto standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0b24-146">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="c0b24-147">V `<standardEndpoints>` části se musí definovat stejný název.</span><span class="sxs-lookup"><span data-stu-id="c0b24-147">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="c0b24-148">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="c0b24-148">isSystemEndpoint</span></span>|<span data-ttu-id="c0b24-149">Logická hodnota určující, zda je koncový bod koncovým bodem infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="c0b24-149">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="c0b24-150">plnění</span><span class="sxs-lookup"><span data-stu-id="c0b24-150">kind</span></span>|<span data-ttu-id="c0b24-151">Řetězec, který určuje typ použitého standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c0b24-151">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="c0b24-152">Typ musí být zaregistrován v `<extensions>` oddílu nebo v souboru Machine. config. Pokud není nic zadáno, vytvoří se běžný koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="c0b24-152">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="c0b24-153">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="c0b24-153">listenUriMode</span></span>|<span data-ttu-id="c0b24-154">Určuje, jak přenos zachází z `ListenUri` poskytované služby k naslouchání.</span><span class="sxs-lookup"><span data-stu-id="c0b24-154">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="c0b24-155">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="c0b24-155">Valid values are</span></span><br /><br /> <span data-ttu-id="c0b24-156">– Explicitní</span><span class="sxs-lookup"><span data-stu-id="c0b24-156">-   Explicit</span></span><br /><span data-ttu-id="c0b24-157">-Unique</span><span class="sxs-lookup"><span data-stu-id="c0b24-157">-   Unique</span></span><br /><br /> <span data-ttu-id="c0b24-158">Výchozí hodnota je explicitní.</span><span class="sxs-lookup"><span data-stu-id="c0b24-158">The default value is Explicit.</span></span>|  
|<span data-ttu-id="c0b24-159">listenUri</span><span class="sxs-lookup"><span data-stu-id="c0b24-159">listenUri</span></span>|<span data-ttu-id="c0b24-160">Řetězec určující identifikátor URI, na kterém naslouchá koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="c0b24-160">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="c0b24-161">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0b24-161">The default is an empty string.</span></span>|  
|<span data-ttu-id="c0b24-162">name</span><span class="sxs-lookup"><span data-stu-id="c0b24-162">name</span></span>|<span data-ttu-id="c0b24-163">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="c0b24-163">Optional attribute.</span></span> <span data-ttu-id="c0b24-164">Řetězec, který určuje název koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="c0b24-164">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="c0b24-165">Výchozí hodnota je zřetězení názvu vazby a názvu popisu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c0b24-165">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="c0b24-166">Služby mohou mít několik koncových bodů, takže `name` atribut koncového bodu se liší od názvu služby.</span><span class="sxs-lookup"><span data-stu-id="c0b24-166">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0b24-167">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c0b24-167">Child Elements</span></span>  
  
|<span data-ttu-id="c0b24-168">Prvek</span><span class="sxs-lookup"><span data-stu-id="c0b24-168">Element</span></span>|<span data-ttu-id="c0b24-169">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b24-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0b24-170">\<headers></span><span class="sxs-lookup"><span data-stu-id="c0b24-170">\<headers></span></span>](headers.md)|<span data-ttu-id="c0b24-171">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="c0b24-171">A collection of address headers.</span></span>|  
|[<span data-ttu-id="c0b24-172">\<identity></span><span class="sxs-lookup"><span data-stu-id="c0b24-172">\<identity></span></span>](identity.md)|<span data-ttu-id="c0b24-173">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0b24-173">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0b24-174">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c0b24-174">Parent Elements</span></span>  
  
|<span data-ttu-id="c0b24-175">Prvek</span><span class="sxs-lookup"><span data-stu-id="c0b24-175">Element</span></span>|<span data-ttu-id="c0b24-176">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b24-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0b24-177">\<service></span><span class="sxs-lookup"><span data-stu-id="c0b24-177">\<service></span></span>](service.md)|<span data-ttu-id="c0b24-178">Konfigurační oddíl definující seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="c0b24-178">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c0b24-179">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0b24-179">Example</span></span>  
 <span data-ttu-id="c0b24-180">Toto je příklad konfigurace koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="c0b24-180">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0b24-181">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0b24-181">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="c0b24-182">Bod Adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="c0b24-182">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="c0b24-183">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="c0b24-183">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
