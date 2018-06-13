---
title: '&lt;endpoint&gt; – &lt;client&gt;'
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f9a69483ab058823fd419edc84868e801b91d2c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748058"
---
# <a name="ltendpointgt-of-ltclientgt"></a><span data-ttu-id="ef0da-102">&lt;endpoint&gt; – &lt;client&gt;</span><span class="sxs-lookup"><span data-stu-id="ef0da-102">&lt;endpoint&gt; of &lt;client&gt;</span></span>
<span data-ttu-id="ef0da-103">Určuje kontrakt, vazbu a vlastnosti adresy koncového bodu kanálu, který je používaný klienty pro připojení ke koncovým bodům služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="ef0da-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="ef0da-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ef0da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef0da-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="ef0da-105">\<client></span></span>  
<span data-ttu-id="ef0da-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="ef0da-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef0da-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef0da-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"  
   behaviorConfiguration="String"  
   binding="String"  
   bindingConfiguration="String"  
   contract="String"   endpointConfiguration="String"   kind="String"  
   name="String"  
</endpoint>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef0da-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ef0da-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ef0da-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ef0da-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef0da-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ef0da-110">Attributes</span></span>  
  
|<span data-ttu-id="ef0da-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ef0da-111">Attribute</span></span>|<span data-ttu-id="ef0da-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ef0da-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef0da-113">adresa</span><span class="sxs-lookup"><span data-stu-id="ef0da-113">address</span></span>|<span data-ttu-id="ef0da-114">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="ef0da-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="ef0da-115">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ef0da-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="ef0da-116">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ef0da-116">The default is an empty string.</span></span> <span data-ttu-id="ef0da-117">Tato adresa musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="ef0da-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="ef0da-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="ef0da-118">behaviorConfiguration</span></span>|<span data-ttu-id="ef0da-119">Řetězec, který obsahuje název chování chování, který se má použít k vytváření instancí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ef0da-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="ef0da-120">Název chování musí být v rozsahu na bod, který je definován službu.</span><span class="sxs-lookup"><span data-stu-id="ef0da-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="ef0da-121">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ef0da-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="ef0da-122">vazba</span><span class="sxs-lookup"><span data-stu-id="ef0da-122">binding</span></span>|<span data-ttu-id="ef0da-123">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="ef0da-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="ef0da-124">Řetězec, který určuje typ vazby použít.</span><span class="sxs-lookup"><span data-stu-id="ef0da-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="ef0da-125">Typ musí mít registrovaný konfigurační oddíl, aby na něj odkazovat.</span><span class="sxs-lookup"><span data-stu-id="ef0da-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="ef0da-126">Typ je registrován podle názvu části místo název typu vazby.</span><span class="sxs-lookup"><span data-stu-id="ef0da-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="ef0da-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="ef0da-127">bindingConfiguration</span></span>|<span data-ttu-id="ef0da-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ef0da-128">Optional.</span></span> <span data-ttu-id="ef0da-129">Řetězec, který obsahuje název konfigurace vazby, který se má použít při vytváření instance koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ef0da-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="ef0da-130">Konfigurace vazeb musí být v rozsahu na bod, který je definován koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ef0da-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="ef0da-131">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ef0da-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ef0da-132">Tento atribut se používá ve spojení s `binding` tak, aby odkazovaly konfigurace konkrétní vazeb v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ef0da-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="ef0da-133">Tento atribut nastavte, pokud se pokoušíte použít vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="ef0da-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="ef0da-134">Jinak může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ef0da-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="ef0da-135">kontrakt</span><span class="sxs-lookup"><span data-stu-id="ef0da-135">contract</span></span>|<span data-ttu-id="ef0da-136">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="ef0da-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="ef0da-137">Řetězec, který určuje, které kontrakt tento koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="ef0da-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="ef0da-138">Sestavení musí implementovat typ smlouvy.</span><span class="sxs-lookup"><span data-stu-id="ef0da-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="ef0da-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="ef0da-139">endpointConfiguration</span></span>|<span data-ttu-id="ef0da-140">Řetězec, který určuje název standardní koncového bodu, který se nastavuje pomocí `kind` atribut, který odkazuje na další konfigurační informace tohoto standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ef0da-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="ef0da-141">Se stejným názvem, musí být definován v `<standardEndpoints>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="ef0da-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="ef0da-142">Typ</span><span class="sxs-lookup"><span data-stu-id="ef0da-142">kind</span></span>|<span data-ttu-id="ef0da-143">Řetězec, který určuje typ standardní koncového bodu použít.</span><span class="sxs-lookup"><span data-stu-id="ef0da-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="ef0da-144">Typ musí být zaregistrovaný ve `<extensions>` části nebo v souboru machine.config. Pokud není zadáno žádné umístění, vytvoří se koncový bod běžné kanálu.</span><span class="sxs-lookup"><span data-stu-id="ef0da-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="ef0da-145">name</span><span class="sxs-lookup"><span data-stu-id="ef0da-145">name</span></span>|<span data-ttu-id="ef0da-146">Volitelný řetězec atributu.</span><span class="sxs-lookup"><span data-stu-id="ef0da-146">Optional string attribute.</span></span> <span data-ttu-id="ef0da-147">Tento atribut jednoznačně identifikuje koncový bod pro danou zakázku.</span><span class="sxs-lookup"><span data-stu-id="ef0da-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="ef0da-148">Můžete definovat více klientů pro daný typ kontrakt.</span><span class="sxs-lookup"><span data-stu-id="ef0da-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="ef0da-149">Každá definice musí rozlišené pomocí jedinečný název konfigurace.</span><span class="sxs-lookup"><span data-stu-id="ef0da-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="ef0da-150">Pokud tento atribut je vynechán, odpovídající koncový bod se používá jako výchozí koncový bod spojená se zadaným typem kontrakt.</span><span class="sxs-lookup"><span data-stu-id="ef0da-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="ef0da-151">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ef0da-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ef0da-152">`name` Atribut vazby se používá pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="ef0da-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef0da-153">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ef0da-153">Child Elements</span></span>  
  
|<span data-ttu-id="ef0da-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="ef0da-154">Element</span></span>|<span data-ttu-id="ef0da-155">Popis</span><span class="sxs-lookup"><span data-stu-id="ef0da-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef0da-156">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="ef0da-156">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="ef0da-157">Kolekce hlavičky adresy.</span><span class="sxs-lookup"><span data-stu-id="ef0da-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="ef0da-158">\<identity ></span><span class="sxs-lookup"><span data-stu-id="ef0da-158">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="ef0da-159">Identita, která umožňuje ověření koncový bod pomocí dalších koncových bodů výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="ef0da-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef0da-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ef0da-160">Parent Elements</span></span>  
  
|<span data-ttu-id="ef0da-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="ef0da-161">Element</span></span>|<span data-ttu-id="ef0da-162">Popis</span><span class="sxs-lookup"><span data-stu-id="ef0da-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef0da-163">\<klient ></span><span class="sxs-lookup"><span data-stu-id="ef0da-163">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="ef0da-164">Konfigurační oddíl, který definuje seznam koncových bodů, které klient může připojit k.</span><span class="sxs-lookup"><span data-stu-id="ef0da-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ef0da-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef0da-165">Example</span></span>  
 <span data-ttu-id="ef0da-166">Toto je příklad konfigurace koncového bodu kanálu.</span><span class="sxs-lookup"><span data-stu-id="ef0da-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"  
    bindingConfiguration="usingDefaults"  
    name="MyBinding"  
    binding="customBinding"  
    contract="HelloWorld">  
</endpoint>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef0da-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef0da-167">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 <xref:System.ServiceModel.Configuration.ClientSection>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>  
 <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>  
 <xref:System.ServiceModel.Configuration.ChannelEndpointElement>  
 [<span data-ttu-id="ef0da-168">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="ef0da-168">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="ef0da-169">Klienti</span><span class="sxs-lookup"><span data-stu-id="ef0da-169">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
