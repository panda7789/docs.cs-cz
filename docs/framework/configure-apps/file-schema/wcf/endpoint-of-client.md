---
title: <endpoint> z <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855317"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="90b82-102">\<endpoint> z \<client></span><span class="sxs-lookup"><span data-stu-id="90b82-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="90b82-103">Určuje kontrakt, vazbu a vlastnosti adresy koncového bodu kanálu, který používají klienti pro připojení ke koncovým bodům služby na serveru.</span><span class="sxs-lookup"><span data-stu-id="90b82-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="90b82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90b82-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90b82-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="90b82-105">Attributes and Elements</span></span>  
 <span data-ttu-id="90b82-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="90b82-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90b82-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="90b82-107">Attributes</span></span>  
  
|<span data-ttu-id="90b82-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="90b82-108">Attribute</span></span>|<span data-ttu-id="90b82-109">Popis</span><span class="sxs-lookup"><span data-stu-id="90b82-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90b82-110">adresa</span><span class="sxs-lookup"><span data-stu-id="90b82-110">address</span></span>|<span data-ttu-id="90b82-111">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="90b82-111">Required string attribute.</span></span><br /><br /> <span data-ttu-id="90b82-112">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="90b82-112">Specifies the address of the endpoint.</span></span> <span data-ttu-id="90b82-113">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="90b82-113">The default is an empty string.</span></span> <span data-ttu-id="90b82-114">Adresa musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="90b82-114">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="90b82-115">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="90b82-115">behaviorConfiguration</span></span>|<span data-ttu-id="90b82-116">Řetězec obsahující název chování, který se má použít k vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="90b82-116">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="90b82-117">Název chování musí být v oboru v místě, kde je služba definovaná.</span><span class="sxs-lookup"><span data-stu-id="90b82-117">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="90b82-118">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="90b82-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="90b82-119">vazba</span><span class="sxs-lookup"><span data-stu-id="90b82-119">binding</span></span>|<span data-ttu-id="90b82-120">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="90b82-120">Required string attribute.</span></span><br /><br /> <span data-ttu-id="90b82-121">Řetězec, který určuje typ vazby, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="90b82-121">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="90b82-122">Typ musí mít registrovaný konfigurační oddíl, aby na něj bylo odkazováno.</span><span class="sxs-lookup"><span data-stu-id="90b82-122">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="90b82-123">Typ je zaregistrován podle názvu oddílu namísto názvu typu vazby.</span><span class="sxs-lookup"><span data-stu-id="90b82-123">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="90b82-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="90b82-124">bindingConfiguration</span></span>|<span data-ttu-id="90b82-125">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="90b82-125">Optional.</span></span> <span data-ttu-id="90b82-126">Řetězec obsahující název konfigurace vazby, která má být použita při vytvoření instance koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="90b82-126">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="90b82-127">Konfigurace vazby musí být v oboru v místě, kde je koncový bod definován.</span><span class="sxs-lookup"><span data-stu-id="90b82-127">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="90b82-128">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="90b82-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="90b82-129">Tento atribut se používá ve spojení s `binding` pro odkazování na konkrétní konfiguraci vazby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="90b82-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="90b82-130">Nastavte tento atribut, pokud se pokoušíte použít vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="90b82-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="90b82-131">V opačném případě může být vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="90b82-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="90b82-132">dodavatele</span><span class="sxs-lookup"><span data-stu-id="90b82-132">contract</span></span>|<span data-ttu-id="90b82-133">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="90b82-133">Required string attribute.</span></span><br /><br /> <span data-ttu-id="90b82-134">Řetězec označující kontrakt, který tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="90b82-134">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="90b82-135">Sestavení musí implementovat typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="90b82-135">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="90b82-136">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="90b82-136">endpointConfiguration</span></span>|<span data-ttu-id="90b82-137">Řetězec, který určuje název standardního koncového bodu, který je nastaven `kind` atributem, který odkazuje na Další informace o konfiguraci tohoto standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="90b82-137">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="90b82-138">V části se musí definovat stejný název `<standardEndpoints>` .</span><span class="sxs-lookup"><span data-stu-id="90b82-138">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="90b82-139">plnění</span><span class="sxs-lookup"><span data-stu-id="90b82-139">kind</span></span>|<span data-ttu-id="90b82-140">Řetězec, který určuje typ použitého standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="90b82-140">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="90b82-141">Typ musí být zaregistrován v `<extensions>` oddílu nebo v souboru Machine. config. Pokud není zadán žádný obsah, je vytvořen běžný koncový bod kanálu.</span><span class="sxs-lookup"><span data-stu-id="90b82-141">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="90b82-142">name</span><span class="sxs-lookup"><span data-stu-id="90b82-142">name</span></span>|<span data-ttu-id="90b82-143">Volitelný řetězcový atribut.</span><span class="sxs-lookup"><span data-stu-id="90b82-143">Optional string attribute.</span></span> <span data-ttu-id="90b82-144">Tento atribut jednoznačně identifikuje koncový bod pro daný kontrakt.</span><span class="sxs-lookup"><span data-stu-id="90b82-144">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="90b82-145">Pro daný typ kontraktu můžete definovat více klientů.</span><span class="sxs-lookup"><span data-stu-id="90b82-145">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="90b82-146">Každá definice musí být odlišena jedinečným názvem konfigurace.</span><span class="sxs-lookup"><span data-stu-id="90b82-146">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="90b82-147">Pokud je tento atribut vynechán, použije se jako výchozí koncový bod přidružený k zadanému typu kontraktu odpovídající koncový bod.</span><span class="sxs-lookup"><span data-stu-id="90b82-147">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="90b82-148">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="90b82-148">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="90b82-149">`name`Atribut vazby se používá pro export definice prostřednictvím WSDL.</span><span class="sxs-lookup"><span data-stu-id="90b82-149">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90b82-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90b82-150">Child Elements</span></span>  
  
|<span data-ttu-id="90b82-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="90b82-151">Element</span></span>|<span data-ttu-id="90b82-152">Description</span><span class="sxs-lookup"><span data-stu-id="90b82-152">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="90b82-153">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="90b82-153">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="90b82-154">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="90b82-154">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90b82-155">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="90b82-155">Parent Elements</span></span>  
  
|<span data-ttu-id="90b82-156">Prvek</span><span class="sxs-lookup"><span data-stu-id="90b82-156">Element</span></span>|<span data-ttu-id="90b82-157">Description</span><span class="sxs-lookup"><span data-stu-id="90b82-157">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="90b82-158">Konfigurační oddíl definující seznam koncových bodů, ke kterým se klient může připojit.</span><span class="sxs-lookup"><span data-stu-id="90b82-158">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="90b82-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="90b82-159">Example</span></span>  
 <span data-ttu-id="90b82-160">Toto je příklad konfigurace koncového bodu kanálu.</span><span class="sxs-lookup"><span data-stu-id="90b82-160">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="90b82-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="90b82-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="90b82-162">Konfigurace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="90b82-162">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="90b82-163">Klienti</span><span class="sxs-lookup"><span data-stu-id="90b82-163">Clients</span></span>](../../../wcf/feature-details/clients.md)
