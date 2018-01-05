---
title: Element &lt;endpoint&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7175cf55df6bb735367effa8f806a472b9ce5ea6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointgt-element"></a><span data-ttu-id="82838-102">Element &lt;endpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="82838-102">&lt;endpoint&gt; element</span></span>
<span data-ttu-id="82838-103">Určuje vazby, kontrakt a vlastnosti adresy pro koncový bod služby, který se používá ke zveřejnění služby.</span><span class="sxs-lookup"><span data-stu-id="82838-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
 <span data-ttu-id="82838-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="82838-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="82838-105">\<služby ></span><span class="sxs-lookup"><span data-stu-id="82838-105">\<service></span></span>  
<span data-ttu-id="82838-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="82838-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82838-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82838-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   bindingName="String"  
   bindingNamespace="String"  
   contract="String"  
   endpointConfiguration="String"   isSystemEndpoint="Boolean"   kind="String"   listenUriMode="Explicit/Unique"  
   listenUri="Uri"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82838-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="82838-108">Attributes and Elements</span></span>  
 <span data-ttu-id="82838-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="82838-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82838-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="82838-110">Attributes</span></span>  
  
|<span data-ttu-id="82838-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="82838-111">Attribute</span></span>|<span data-ttu-id="82838-112">Popis</span><span class="sxs-lookup"><span data-stu-id="82838-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82838-113">adresa</span><span class="sxs-lookup"><span data-stu-id="82838-113">address</span></span>|<span data-ttu-id="82838-114">Řetězec, který obsahuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="82838-114">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="82838-115">Adresu lze zadat jako absolutní nebo relativní adresa.</span><span class="sxs-lookup"><span data-stu-id="82838-115">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="82838-116">Pokud je zadaný relativní adresa, hostitel se očekává poskytování základní adresu, která je vhodná pro používané vazba schéma přenosu.</span><span class="sxs-lookup"><span data-stu-id="82838-116">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="82838-117">Pokud adresa není nakonfigurována, základní adresu se považuje za adresu pro tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="82838-117">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="82838-118">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="82838-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="82838-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="82838-119">behaviorConfiguration</span></span>|<span data-ttu-id="82838-120">Řetězec, který obsahuje název chování, který se má použít v koncovém bodě.</span><span class="sxs-lookup"><span data-stu-id="82838-120">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="82838-121">vazba</span><span class="sxs-lookup"><span data-stu-id="82838-121">binding</span></span>|<span data-ttu-id="82838-122">Vyžaduje atribut řetězce, který určuje typ vazby použít.</span><span class="sxs-lookup"><span data-stu-id="82838-122">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="82838-123">Typ musí mít registrovaný konfigurační oddíl, aby na něj odkazovat.</span><span class="sxs-lookup"><span data-stu-id="82838-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="82838-124">Typ je zaregistrovanou podle názvu části, nikoli název typu vazby.</span><span class="sxs-lookup"><span data-stu-id="82838-124">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="82838-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="82838-125">bindingConfiguration</span></span>|<span data-ttu-id="82838-126">Řetězec, který určuje název vazby vazby pro použití při vytváření instance koncový bod.</span><span class="sxs-lookup"><span data-stu-id="82838-126">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="82838-127">Název vazby musí být v rozsahu na bod, který je definován koncový bod.</span><span class="sxs-lookup"><span data-stu-id="82838-127">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="82838-128">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="82838-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="82838-129">Tento atribut se používá ve spojení s `binding` tak, aby odkazovaly konfigurace konkrétní vazeb v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="82838-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="82838-130">Tento atribut nastavte, pokud se pokoušíte použít vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="82838-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="82838-131">Jinak může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="82838-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="82838-132">bindingName</span><span class="sxs-lookup"><span data-stu-id="82838-132">bindingName</span></span>|<span data-ttu-id="82838-133">Řetězec, který určuje jedinečný název kvalifikovaný vazby pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="82838-133">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="82838-134">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="82838-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="82838-135">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="82838-135">bindingNamespace</span></span>|<span data-ttu-id="82838-136">Řetězec, který určuje kvalifikovaný název oboru názvů vazby pro definici exportovat prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="82838-136">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="82838-137">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="82838-137">The default is an empty string.</span></span>|  
|<span data-ttu-id="82838-138">kontrakt</span><span class="sxs-lookup"><span data-stu-id="82838-138">contract</span></span>|<span data-ttu-id="82838-139">Řetězec, který určuje, které kontrakt tento koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="82838-139">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="82838-140">Sestavení musí implementovat typ smlouvy.</span><span class="sxs-lookup"><span data-stu-id="82838-140">The assembly must implement the contract type.</span></span> <span data-ttu-id="82838-141">Pokud implementace služby implementuje typu jeden kontrakt, můžete tuto vlastnost vynechat.</span><span class="sxs-lookup"><span data-stu-id="82838-141">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="82838-142">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="82838-142">The default is an empty string.</span></span>|  
|<span data-ttu-id="82838-143">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="82838-143">endpointConfiguration</span></span>|<span data-ttu-id="82838-144">Řetězec, který určuje název standardní koncového bodu, který se nastavuje pomocí `kind` atribut, který odkazuje na další konfigurační informace tohoto standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="82838-144">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="82838-145">Se stejným názvem, musí být definován v `<standardEndpoints>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="82838-145">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="82838-146">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="82838-146">isSystemEndpoint</span></span>|<span data-ttu-id="82838-147">Logická hodnota, která určuje, jestli koncový bod je koncový bod infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="82838-147">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="82838-148">Typ</span><span class="sxs-lookup"><span data-stu-id="82838-148">kind</span></span>|<span data-ttu-id="82838-149">Řetězec, který určuje typ standardní koncového bodu použít.</span><span class="sxs-lookup"><span data-stu-id="82838-149">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="82838-150">Typ musí být zaregistrovaný ve `<extensions>` části nebo v souboru machine.config. Pokud není zadáno žádné umístění, vytvoří se běžné koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="82838-150">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="82838-151">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="82838-151">listenUriMode</span></span>|<span data-ttu-id="82838-152">Určuje, jak zpracovává přenos `ListenUri` zadaný pro službu pro naslouchání.</span><span class="sxs-lookup"><span data-stu-id="82838-152">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="82838-153">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="82838-153">Valid values are</span></span><br /><br /> <span data-ttu-id="82838-154">-Explicitní</span><span class="sxs-lookup"><span data-stu-id="82838-154">-   Explicit</span></span><br /><span data-ttu-id="82838-155">-Jedinečné</span><span class="sxs-lookup"><span data-stu-id="82838-155">-   Unique</span></span><br /><br /> <span data-ttu-id="82838-156">Výchozí hodnota je explicitní.</span><span class="sxs-lookup"><span data-stu-id="82838-156">The default value is Explicit.</span></span>|  
|<span data-ttu-id="82838-157">Adrese ListenUri</span><span class="sxs-lookup"><span data-stu-id="82838-157">listenUri</span></span>|<span data-ttu-id="82838-158">Řetězec, který určuje identifikátor URI, na kterém naslouchá koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="82838-158">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="82838-159">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="82838-159">The default is an empty string.</span></span>|  
|<span data-ttu-id="82838-160">name</span><span class="sxs-lookup"><span data-stu-id="82838-160">name</span></span>|<span data-ttu-id="82838-161">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="82838-161">Optional attribute.</span></span> <span data-ttu-id="82838-162">Řetězec, který určuje název koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="82838-162">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="82838-163">Výchozí hodnota je zřetězení vazby název a popis názvu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="82838-163">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="82838-164">Služby mohou mít několik koncových bodů, takže pro koncový bod `name` atributu se liší od názvu služby.</span><span class="sxs-lookup"><span data-stu-id="82838-164">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82838-165">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="82838-165">Child Elements</span></span>  
  
|<span data-ttu-id="82838-166">Prvek</span><span class="sxs-lookup"><span data-stu-id="82838-166">Element</span></span>|<span data-ttu-id="82838-167">Popis</span><span class="sxs-lookup"><span data-stu-id="82838-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82838-168">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="82838-168">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="82838-169">Kolekce hlavičky adresy.</span><span class="sxs-lookup"><span data-stu-id="82838-169">A collection of address headers.</span></span>|  
|[<span data-ttu-id="82838-170">\<identity ></span><span class="sxs-lookup"><span data-stu-id="82838-170">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="82838-171">Identita, která umožňuje ověření koncový bod pomocí dalších koncových bodů výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="82838-171">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82838-172">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="82838-172">Parent Elements</span></span>  
  
|<span data-ttu-id="82838-173">Prvek</span><span class="sxs-lookup"><span data-stu-id="82838-173">Element</span></span>|<span data-ttu-id="82838-174">Popis</span><span class="sxs-lookup"><span data-stu-id="82838-174">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82838-175">\<služby ></span><span class="sxs-lookup"><span data-stu-id="82838-175">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="82838-176">Konfigurační oddíl, který definuje seznam koncových bodů, které klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="82838-176">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82838-177">Příklad</span><span class="sxs-lookup"><span data-stu-id="82838-177">Example</span></span>  
 <span data-ttu-id="82838-178">Toto je příklad konfigurace koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="82838-178">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint   
    address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    bindingName="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
    <Headers>  
       <Region xmlns="http://tempuri.org/">EastCoast</Region>  
       <Member xmlns="http://tempuri.org/">Gold</Member>  
    </Headers>  
</endpoint>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82838-179">Viz také</span><span class="sxs-lookup"><span data-stu-id="82838-179">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceEndpointElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.Description.ServiceEndpoint>  
 [<span data-ttu-id="82838-180">Koncové body: adresy, vazby a kontrakty</span><span class="sxs-lookup"><span data-stu-id="82838-180">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="82838-181">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="82838-181">How to: Create a Service Endpoint in Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
