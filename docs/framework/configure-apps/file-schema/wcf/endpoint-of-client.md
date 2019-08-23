---
title: <endpoint> z <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 2bf59972ff2f75995e94a3c1934e88944d65fcc7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919100"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="8c8d2-102">\<koncový bod > \<> klienta</span><span class="sxs-lookup"><span data-stu-id="8c8d2-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="8c8d2-103">Určuje kontrakt, vazbu a vlastnosti adresy koncového bodu kanálu, který používají klienti pro připojení ke koncovým bodům služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="8c8d2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8c8d2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8c8d2-105">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="8c8d2-105">\<client></span></span>  
<span data-ttu-id="8c8d2-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="8c8d2-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8d2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c8d2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c8d2-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8c8d2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8c8d2-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c8d2-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8c8d2-110">Attributes</span></span>  
  
|<span data-ttu-id="8c8d2-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8c8d2-111">Attribute</span></span>|<span data-ttu-id="8c8d2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8c8d2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c8d2-113">adresa</span><span class="sxs-lookup"><span data-stu-id="8c8d2-113">address</span></span>|<span data-ttu-id="8c8d2-114">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="8c8d2-115">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="8c8d2-116">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-116">The default is an empty string.</span></span> <span data-ttu-id="8c8d2-117">Adresa musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="8c8d2-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="8c8d2-118">behaviorConfiguration</span></span>|<span data-ttu-id="8c8d2-119">Řetězec obsahující název chování, který se má použít k vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="8c8d2-120">Název chování musí být v oboru v místě, kde je služba definovaná.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="8c8d2-121">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="8c8d2-122">vazba</span><span class="sxs-lookup"><span data-stu-id="8c8d2-122">binding</span></span>|<span data-ttu-id="8c8d2-123">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="8c8d2-124">Řetězec, který určuje typ vazby, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="8c8d2-125">Typ musí mít registrovaný konfigurační oddíl, aby na něj bylo odkazováno.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="8c8d2-126">Typ je zaregistrován podle názvu oddílu namísto názvu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="8c8d2-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="8c8d2-127">bindingConfiguration</span></span>|<span data-ttu-id="8c8d2-128">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-128">Optional.</span></span> <span data-ttu-id="8c8d2-129">Řetězec obsahující název konfigurace vazby, která má být použita při vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="8c8d2-130">Konfigurace vazby musí být v oboru v místě, kde je koncový bod definován.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="8c8d2-131">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="8c8d2-132">Tento atribut se používá ve spojení s `binding` pro odkazování na konkrétní konfiguraci vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="8c8d2-133">Nastavte tento atribut, pokud se pokoušíte použít vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="8c8d2-134">V opačném případě může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="8c8d2-135">dodavatele</span><span class="sxs-lookup"><span data-stu-id="8c8d2-135">contract</span></span>|<span data-ttu-id="8c8d2-136">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="8c8d2-137">Řetězec označující kontrakt, který tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="8c8d2-138">Sestavení musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="8c8d2-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="8c8d2-139">endpointConfiguration</span></span>|<span data-ttu-id="8c8d2-140">Řetězec, který určuje název standardního koncového bodu, který je nastaven `kind` atributem, který odkazuje na Další informace o konfiguraci tohoto standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="8c8d2-141">V `<standardEndpoints>` části se musí definovat stejný název.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="8c8d2-142">plnění</span><span class="sxs-lookup"><span data-stu-id="8c8d2-142">kind</span></span>|<span data-ttu-id="8c8d2-143">Řetězec, který určuje typ použitého standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="8c8d2-144">Typ musí být zaregistrován v `<extensions>` oddílu nebo v souboru Machine. config. Pokud není zadán žádný obsah, je vytvořen běžný koncový bod kanálu.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="8c8d2-145">name</span><span class="sxs-lookup"><span data-stu-id="8c8d2-145">name</span></span>|<span data-ttu-id="8c8d2-146">Volitelný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-146">Optional string attribute.</span></span> <span data-ttu-id="8c8d2-147">Tento atribut jednoznačně identifikuje koncový bod pro daný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="8c8d2-148">Pro daný typ kontraktu můžete definovat více klientů.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="8c8d2-149">Každá definice musí být odlišena jedinečným názvem konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="8c8d2-150">Pokud je tento atribut vynechán, použije se jako výchozí koncový bod přidružený k zadanému typu kontraktu odpovídající koncový bod.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="8c8d2-151">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="8c8d2-152">`name` Atribut vazby se používá pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c8d2-153">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8c8d2-153">Child Elements</span></span>  
  
|<span data-ttu-id="8c8d2-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c8d2-154">Element</span></span>|<span data-ttu-id="8c8d2-155">Popis</span><span class="sxs-lookup"><span data-stu-id="8c8d2-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c8d2-156">\<headers></span><span class="sxs-lookup"><span data-stu-id="8c8d2-156">\<headers></span></span>](headers.md)|<span data-ttu-id="8c8d2-157">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="8c8d2-158">\<identity></span><span class="sxs-lookup"><span data-stu-id="8c8d2-158">\<identity></span></span>](identity.md)|<span data-ttu-id="8c8d2-159">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c8d2-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8c8d2-160">Parent Elements</span></span>  
  
|<span data-ttu-id="8c8d2-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c8d2-161">Element</span></span>|<span data-ttu-id="8c8d2-162">Popis</span><span class="sxs-lookup"><span data-stu-id="8c8d2-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c8d2-163">\<client></span><span class="sxs-lookup"><span data-stu-id="8c8d2-163">\<client></span></span>](client.md)|<span data-ttu-id="8c8d2-164">Konfigurační oddíl definující seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8c8d2-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c8d2-165">Example</span></span>  
 <span data-ttu-id="8c8d2-166">Toto je příklad konfigurace koncového bodu kanálu.</span><span class="sxs-lookup"><span data-stu-id="8c8d2-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="8c8d2-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c8d2-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="8c8d2-168">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="8c8d2-168">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="8c8d2-169">Klienti</span><span class="sxs-lookup"><span data-stu-id="8c8d2-169">Clients</span></span>](../../../wcf/feature-details/clients.md)
