---
title: <endpoint> z <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 3af41ad5b5681b08aac44d984372ab5ac66caf5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231198"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="2906e-102">\<koncový bod > z \<klienta ></span><span class="sxs-lookup"><span data-stu-id="2906e-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="2906e-103">Určuje kontrakt vazby a vlastnosti adresy koncového bodu kanálu, který používají klienti pro připojení ke koncovým bodům služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="2906e-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="2906e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2906e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2906e-105">\<client></span><span class="sxs-lookup"><span data-stu-id="2906e-105">\<client></span></span>  
<span data-ttu-id="2906e-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="2906e-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2906e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2906e-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2906e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2906e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2906e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2906e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2906e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2906e-110">Attributes</span></span>  
  
|<span data-ttu-id="2906e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2906e-111">Attribute</span></span>|<span data-ttu-id="2906e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2906e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2906e-113">adresa</span><span class="sxs-lookup"><span data-stu-id="2906e-113">address</span></span>|<span data-ttu-id="2906e-114">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="2906e-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="2906e-115">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2906e-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="2906e-116">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2906e-116">The default is an empty string.</span></span> <span data-ttu-id="2906e-117">Tato adresa musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="2906e-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="2906e-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="2906e-118">behaviorConfiguration</span></span>|<span data-ttu-id="2906e-119">Řetězec obsahující název chování, jenž bude použit k vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2906e-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="2906e-120">Název musí být v rozsahu od bodu služby je definována.</span><span class="sxs-lookup"><span data-stu-id="2906e-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="2906e-121">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2906e-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="2906e-122">vazba</span><span class="sxs-lookup"><span data-stu-id="2906e-122">binding</span></span>|<span data-ttu-id="2906e-123">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="2906e-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="2906e-124">Řetězec, který označuje typ použité vazby.</span><span class="sxs-lookup"><span data-stu-id="2906e-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="2906e-125">Typ musí mít registrované konfigurační oddíl pro odkazovat.</span><span class="sxs-lookup"><span data-stu-id="2906e-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="2906e-126">Název oddílu, zaregistrován typ místo podle názvu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="2906e-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="2906e-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2906e-127">bindingConfiguration</span></span>|<span data-ttu-id="2906e-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2906e-128">Optional.</span></span> <span data-ttu-id="2906e-129">Řetězec, který obsahuje název konfigurace vazby, která se použije při vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2906e-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="2906e-130">Konfigurace vazby musí být v rozsahu od bodu na koncový bod je definována.</span><span class="sxs-lookup"><span data-stu-id="2906e-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="2906e-131">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2906e-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2906e-132">Tento atribut se používá ve spojení s `binding` odkazovat konfigurace konkrétní vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="2906e-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="2906e-133">Tento atribut nastavte, pokud se pokoušíte použít vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="2906e-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="2906e-134">V opačném případě může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2906e-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="2906e-135">kontrakt</span><span class="sxs-lookup"><span data-stu-id="2906e-135">contract</span></span>|<span data-ttu-id="2906e-136">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="2906e-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="2906e-137">Řetězec označující kontrakt, který tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="2906e-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="2906e-138">Sestavení musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="2906e-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="2906e-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="2906e-139">endpointConfiguration</span></span>|<span data-ttu-id="2906e-140">Řetězec určující název standardního koncového bodu, který je nastaven podle `kind` atribut, který odkazuje na další konfigurační informace tohoto standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2906e-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="2906e-141">Se stejným názvem musí být definován v `<standardEndpoints>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="2906e-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="2906e-142">Typ</span><span class="sxs-lookup"><span data-stu-id="2906e-142">kind</span></span>|<span data-ttu-id="2906e-143">Řetězec, který určuje typ standardně použitého koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="2906e-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="2906e-144">Typ musí být zaregistrovaný ve `<extensions>` části nebo v souboru machine.config. Pokud není zadáno žádné umístění, vytvoří se běžné koncového bodu kanálu.</span><span class="sxs-lookup"><span data-stu-id="2906e-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="2906e-145">name</span><span class="sxs-lookup"><span data-stu-id="2906e-145">name</span></span>|<span data-ttu-id="2906e-146">Volitelný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="2906e-146">Optional string attribute.</span></span> <span data-ttu-id="2906e-147">Tento atribut jednoznačně identifikuje koncový bod pro daný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="2906e-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="2906e-148">Můžete definovat více klientů pro daný typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="2906e-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="2906e-149">Každá definice musí možné odlišit použitím jedinečný název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2906e-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="2906e-150">Pokud tento atribut je vynechán, odpovídající koncový bod se používá jako výchozí koncový bod spojený se zadaným typem kontraktu.</span><span class="sxs-lookup"><span data-stu-id="2906e-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="2906e-151">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2906e-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2906e-152">`name` Atribut vazby se používá pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="2906e-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2906e-153">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2906e-153">Child Elements</span></span>  
  
|<span data-ttu-id="2906e-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="2906e-154">Element</span></span>|<span data-ttu-id="2906e-155">Popis</span><span class="sxs-lookup"><span data-stu-id="2906e-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2906e-156">\<headers></span><span class="sxs-lookup"><span data-stu-id="2906e-156">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="2906e-157">Kolekce záhlaví adres.</span><span class="sxs-lookup"><span data-stu-id="2906e-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="2906e-158">\<identity></span><span class="sxs-lookup"><span data-stu-id="2906e-158">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2906e-159">Identita, která umožňuje ověřování z koncového bodu jiné koncové body výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="2906e-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2906e-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2906e-160">Parent Elements</span></span>  
  
|<span data-ttu-id="2906e-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="2906e-161">Element</span></span>|<span data-ttu-id="2906e-162">Popis</span><span class="sxs-lookup"><span data-stu-id="2906e-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2906e-163">\<client></span><span class="sxs-lookup"><span data-stu-id="2906e-163">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="2906e-164">Konfigurační oddíl, který definuje seznam koncových bodů, které se klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="2906e-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2906e-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="2906e-165">Example</span></span>  
 <span data-ttu-id="2906e-166">Toto je příklad konfigurace koncového bodu kanálu.</span><span class="sxs-lookup"><span data-stu-id="2906e-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="2906e-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2906e-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="2906e-168">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="2906e-168">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="2906e-169">Klienti</span><span class="sxs-lookup"><span data-stu-id="2906e-169">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
