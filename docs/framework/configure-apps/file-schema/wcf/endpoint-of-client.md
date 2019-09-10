---
title: <endpoint> z <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855317"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="fc43c-102">\<koncový bod > \<> klienta</span><span class="sxs-lookup"><span data-stu-id="fc43c-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="fc43c-103">Určuje kontrakt, vazbu a vlastnosti adresy koncového bodu kanálu, který používají klienti pro připojení ke koncovým bodům služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="fc43c-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
<span data-ttu-id="fc43c-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fc43c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fc43c-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fc43c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fc43c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="fc43c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="fc43c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> koncového bodu**</span><span class="sxs-lookup"><span data-stu-id="fc43c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc43c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc43c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc43c-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fc43c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fc43c-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fc43c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc43c-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="fc43c-111">Attributes</span></span>  
  
|<span data-ttu-id="fc43c-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="fc43c-112">Attribute</span></span>|<span data-ttu-id="fc43c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="fc43c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc43c-114">adresa</span><span class="sxs-lookup"><span data-stu-id="fc43c-114">address</span></span>|<span data-ttu-id="fc43c-115">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="fc43c-115">Required string attribute.</span></span><br /><br /> <span data-ttu-id="fc43c-116">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fc43c-116">Specifies the address of the endpoint.</span></span> <span data-ttu-id="fc43c-117">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fc43c-117">The default is an empty string.</span></span> <span data-ttu-id="fc43c-118">Adresa musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="fc43c-118">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="fc43c-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc43c-119">behaviorConfiguration</span></span>|<span data-ttu-id="fc43c-120">Řetězec obsahující název chování, který se má použít k vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fc43c-120">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="fc43c-121">Název chování musí být v oboru v místě, kde je služba definovaná.</span><span class="sxs-lookup"><span data-stu-id="fc43c-121">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="fc43c-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fc43c-122">The default is an empty string.</span></span>|  
|<span data-ttu-id="fc43c-123">vazba</span><span class="sxs-lookup"><span data-stu-id="fc43c-123">binding</span></span>|<span data-ttu-id="fc43c-124">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="fc43c-124">Required string attribute.</span></span><br /><br /> <span data-ttu-id="fc43c-125">Řetězec, který určuje typ vazby, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="fc43c-125">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="fc43c-126">Typ musí mít registrovaný konfigurační oddíl, aby na něj bylo odkazováno.</span><span class="sxs-lookup"><span data-stu-id="fc43c-126">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="fc43c-127">Typ je zaregistrován podle názvu oddílu namísto názvu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="fc43c-127">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="fc43c-128">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc43c-128">bindingConfiguration</span></span>|<span data-ttu-id="fc43c-129">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="fc43c-129">Optional.</span></span> <span data-ttu-id="fc43c-130">Řetězec obsahující název konfigurace vazby, která má být použita při vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fc43c-130">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="fc43c-131">Konfigurace vazby musí být v oboru v místě, kde je koncový bod definován.</span><span class="sxs-lookup"><span data-stu-id="fc43c-131">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="fc43c-132">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fc43c-132">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="fc43c-133">Tento atribut se používá ve spojení s `binding` pro odkazování na konkrétní konfiguraci vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="fc43c-133">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="fc43c-134">Nastavte tento atribut, pokud se pokoušíte použít vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="fc43c-134">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="fc43c-135">V opačném případě může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="fc43c-135">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="fc43c-136">Dodavatele</span><span class="sxs-lookup"><span data-stu-id="fc43c-136">contract</span></span>|<span data-ttu-id="fc43c-137">Požadovaný atribut typu string.</span><span class="sxs-lookup"><span data-stu-id="fc43c-137">Required string attribute.</span></span><br /><br /> <span data-ttu-id="fc43c-138">Řetězec označující kontrakt, který tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="fc43c-138">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="fc43c-139">Sestavení musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="fc43c-139">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="fc43c-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc43c-140">endpointConfiguration</span></span>|<span data-ttu-id="fc43c-141">Řetězec, který určuje název standardního koncového bodu, který je nastaven `kind` atributem, který odkazuje na Další informace o konfiguraci tohoto standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fc43c-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="fc43c-142">V `<standardEndpoints>` části se musí definovat stejný název.</span><span class="sxs-lookup"><span data-stu-id="fc43c-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="fc43c-143">plnění</span><span class="sxs-lookup"><span data-stu-id="fc43c-143">kind</span></span>|<span data-ttu-id="fc43c-144">Řetězec, který určuje typ použitého standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fc43c-144">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="fc43c-145">Typ musí být zaregistrován v `<extensions>` oddílu nebo v souboru Machine. config. Pokud není zadán žádný obsah, je vytvořen běžný koncový bod kanálu.</span><span class="sxs-lookup"><span data-stu-id="fc43c-145">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="fc43c-146">name</span><span class="sxs-lookup"><span data-stu-id="fc43c-146">name</span></span>|<span data-ttu-id="fc43c-147">Volitelný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="fc43c-147">Optional string attribute.</span></span> <span data-ttu-id="fc43c-148">Tento atribut jednoznačně identifikuje koncový bod pro daný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fc43c-148">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="fc43c-149">Pro daný typ kontraktu můžete definovat více klientů.</span><span class="sxs-lookup"><span data-stu-id="fc43c-149">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="fc43c-150">Každá definice musí být odlišena jedinečným názvem konfigurace.</span><span class="sxs-lookup"><span data-stu-id="fc43c-150">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="fc43c-151">Pokud je tento atribut vynechán, použije se jako výchozí koncový bod přidružený k zadanému typu kontraktu odpovídající koncový bod.</span><span class="sxs-lookup"><span data-stu-id="fc43c-151">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="fc43c-152">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fc43c-152">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="fc43c-153">`name` Atribut vazby se používá pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="fc43c-153">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc43c-154">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fc43c-154">Child Elements</span></span>  
  
|<span data-ttu-id="fc43c-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc43c-155">Element</span></span>|<span data-ttu-id="fc43c-156">Popis</span><span class="sxs-lookup"><span data-stu-id="fc43c-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc43c-157">\<headers></span><span class="sxs-lookup"><span data-stu-id="fc43c-157">\<headers></span></span>](headers.md)|<span data-ttu-id="fc43c-158">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="fc43c-158">A collection of address headers.</span></span>|  
|[<span data-ttu-id="fc43c-159">\<identity></span><span class="sxs-lookup"><span data-stu-id="fc43c-159">\<identity></span></span>](identity.md)|<span data-ttu-id="fc43c-160">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="fc43c-160">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc43c-161">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fc43c-161">Parent Elements</span></span>  
  
|<span data-ttu-id="fc43c-162">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc43c-162">Element</span></span>|<span data-ttu-id="fc43c-163">Popis</span><span class="sxs-lookup"><span data-stu-id="fc43c-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc43c-164">\<client></span><span class="sxs-lookup"><span data-stu-id="fc43c-164">\<client></span></span>](client.md)|<span data-ttu-id="fc43c-165">Konfigurační oddíl definující seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="fc43c-165">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fc43c-166">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc43c-166">Example</span></span>  
 <span data-ttu-id="fc43c-167">Toto je příklad konfigurace koncového bodu kanálu.</span><span class="sxs-lookup"><span data-stu-id="fc43c-167">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="fc43c-168">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc43c-168">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="fc43c-169">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="fc43c-169">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="fc43c-170">Klienti</span><span class="sxs-lookup"><span data-stu-id="fc43c-170">Clients</span></span>](../../../wcf/feature-details/clients.md)
