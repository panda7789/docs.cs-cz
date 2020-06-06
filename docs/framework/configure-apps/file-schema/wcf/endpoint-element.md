---
title: <endpoint> – element
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: fb9d3bf9b5f1a742abcc70d78af026c179ec4c4d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855390"
---
# <a name="endpoint-element"></a><span data-ttu-id="54f27-102">\<endpoint> – element</span><span class="sxs-lookup"><span data-stu-id="54f27-102">\<endpoint> element</span></span>
<span data-ttu-id="54f27-103">Určuje vazbu, kontrakt a vlastnosti adresy koncového bodu služby, který slouží k vystavení služeb.</span><span class="sxs-lookup"><span data-stu-id="54f27-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="54f27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54f27-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54f27-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="54f27-105">Attributes and Elements</span></span>  
 <span data-ttu-id="54f27-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="54f27-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54f27-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="54f27-107">Attributes</span></span>  
  
|<span data-ttu-id="54f27-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="54f27-108">Attribute</span></span>|<span data-ttu-id="54f27-109">Popis</span><span class="sxs-lookup"><span data-stu-id="54f27-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54f27-110">adresa</span><span class="sxs-lookup"><span data-stu-id="54f27-110">address</span></span>|<span data-ttu-id="54f27-111">Řetězec, který obsahuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="54f27-111">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="54f27-112">Adresu lze zadat jako absolutní nebo relativní adresu.</span><span class="sxs-lookup"><span data-stu-id="54f27-112">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="54f27-113">Pokud je zadána relativní adresa, očekává se, že hostitel poskytne základní adresu vhodnou pro přenosové schéma používané ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="54f27-113">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="54f27-114">Pokud není adresa nakonfigurovaná, předpokládá se, že základní adresa je adresa pro tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="54f27-114">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="54f27-115">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="54f27-115">The default is an empty string.</span></span>|  
|<span data-ttu-id="54f27-116">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="54f27-116">behaviorConfiguration</span></span>|<span data-ttu-id="54f27-117">Řetězec obsahující název chování, které se má použít v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="54f27-117">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="54f27-118">vazba</span><span class="sxs-lookup"><span data-stu-id="54f27-118">binding</span></span>|<span data-ttu-id="54f27-119">Povinný atribut řetězce, který určuje typ vazby, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="54f27-119">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="54f27-120">Typ musí mít registrovaný konfigurační oddíl, aby na něj bylo odkazováno.</span><span class="sxs-lookup"><span data-stu-id="54f27-120">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="54f27-121">Typ je zaregistrován podle názvu oddílu, nikoli podle názvu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="54f27-121">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="54f27-122">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="54f27-122">bindingConfiguration</span></span>|<span data-ttu-id="54f27-123">Řetězec, který určuje název vazby vazby, která se má použít při vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="54f27-123">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="54f27-124">Název vazby musí být v oboru v místě, kde je koncový bod definován.</span><span class="sxs-lookup"><span data-stu-id="54f27-124">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="54f27-125">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="54f27-125">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="54f27-126">Tento atribut se používá ve spojení s `binding` pro odkazování na konkrétní konfiguraci vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="54f27-126">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="54f27-127">Nastavte tento atribut, pokud se pokoušíte použít vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="54f27-127">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="54f27-128">V opačném případě může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="54f27-128">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="54f27-129">Binding</span><span class="sxs-lookup"><span data-stu-id="54f27-129">bindingName</span></span>|<span data-ttu-id="54f27-130">Řetězec, který určuje jedinečný kvalifikovaný název vazby pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="54f27-130">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="54f27-131">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="54f27-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="54f27-132">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="54f27-132">bindingNamespace</span></span>|<span data-ttu-id="54f27-133">Řetězec, který určuje kvalifikovaný název oboru názvů vazby pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="54f27-133">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="54f27-134">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="54f27-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="54f27-135">dodavatele</span><span class="sxs-lookup"><span data-stu-id="54f27-135">contract</span></span>|<span data-ttu-id="54f27-136">Řetězec označující kontrakt, který tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="54f27-136">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="54f27-137">Sestavení musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="54f27-137">The assembly must implement the contract type.</span></span> <span data-ttu-id="54f27-138">Pokud implementace služby implementuje jeden typ kontraktu, může být tato vlastnost vynechána.</span><span class="sxs-lookup"><span data-stu-id="54f27-138">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="54f27-139">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="54f27-139">The default is an empty string.</span></span>|  
|<span data-ttu-id="54f27-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="54f27-140">endpointConfiguration</span></span>|<span data-ttu-id="54f27-141">Řetězec, který určuje název standardního koncového bodu, který je nastaven `kind` atributem, který odkazuje na Další informace o konfiguraci tohoto standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="54f27-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="54f27-142">V části se musí definovat stejný název `<standardEndpoints>` .</span><span class="sxs-lookup"><span data-stu-id="54f27-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="54f27-143">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="54f27-143">isSystemEndpoint</span></span>|<span data-ttu-id="54f27-144">Logická hodnota určující, zda je koncový bod koncovým bodem infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="54f27-144">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="54f27-145">plnění</span><span class="sxs-lookup"><span data-stu-id="54f27-145">kind</span></span>|<span data-ttu-id="54f27-146">Řetězec, který určuje typ použitého standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="54f27-146">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="54f27-147">Typ musí být zaregistrován v `<extensions>` oddílu nebo v souboru Machine. config. Pokud není nic zadáno, vytvoří se běžný koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="54f27-147">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="54f27-148">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="54f27-148">listenUriMode</span></span>|<span data-ttu-id="54f27-149">Určuje, jak přenos zachází z `ListenUri` poskytované služby k naslouchání.</span><span class="sxs-lookup"><span data-stu-id="54f27-149">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="54f27-150">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="54f27-150">Valid values are</span></span><br /><br /> <span data-ttu-id="54f27-151">– Explicitní</span><span class="sxs-lookup"><span data-stu-id="54f27-151">-   Explicit</span></span><br /><span data-ttu-id="54f27-152">-Unique</span><span class="sxs-lookup"><span data-stu-id="54f27-152">-   Unique</span></span><br /><br /> <span data-ttu-id="54f27-153">Výchozí hodnota je explicitní.</span><span class="sxs-lookup"><span data-stu-id="54f27-153">The default value is Explicit.</span></span>|  
|<span data-ttu-id="54f27-154">listenUri</span><span class="sxs-lookup"><span data-stu-id="54f27-154">listenUri</span></span>|<span data-ttu-id="54f27-155">Řetězec určující identifikátor URI, na kterém naslouchá koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="54f27-155">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="54f27-156">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="54f27-156">The default is an empty string.</span></span>|  
|<span data-ttu-id="54f27-157">name</span><span class="sxs-lookup"><span data-stu-id="54f27-157">name</span></span>|<span data-ttu-id="54f27-158">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="54f27-158">Optional attribute.</span></span> <span data-ttu-id="54f27-159">Řetězec, který určuje název koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="54f27-159">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="54f27-160">Výchozí hodnota je zřetězení názvu vazby a názvu popisu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="54f27-160">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="54f27-161">Služby mohou mít několik koncových bodů, takže atribut koncového bodu `name` se liší od názvu služby.</span><span class="sxs-lookup"><span data-stu-id="54f27-161">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54f27-162">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="54f27-162">Child Elements</span></span>  
  
|<span data-ttu-id="54f27-163">Prvek</span><span class="sxs-lookup"><span data-stu-id="54f27-163">Element</span></span>|<span data-ttu-id="54f27-164">Description</span><span class="sxs-lookup"><span data-stu-id="54f27-164">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="54f27-165">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="54f27-165">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="54f27-166">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="54f27-166">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54f27-167">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="54f27-167">Parent Elements</span></span>  
  
|<span data-ttu-id="54f27-168">Prvek</span><span class="sxs-lookup"><span data-stu-id="54f27-168">Element</span></span>|<span data-ttu-id="54f27-169">Description</span><span class="sxs-lookup"><span data-stu-id="54f27-169">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="54f27-170">Konfigurační oddíl definující seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="54f27-170">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="54f27-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="54f27-171">Example</span></span>  
 <span data-ttu-id="54f27-172">Toto je příklad konfigurace koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="54f27-172">This is an example of a service endpoint configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54f27-173">Viz také</span><span class="sxs-lookup"><span data-stu-id="54f27-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="54f27-174">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="54f27-174">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="54f27-175">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="54f27-175">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
