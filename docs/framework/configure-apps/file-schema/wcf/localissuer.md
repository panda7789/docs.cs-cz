---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 4ec5a99139112ae600c1c2bc44feb6d3f62da1e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931741"
---
# <a name="localissuer"></a><span data-ttu-id="336ab-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="336ab-101">\<localIssuer></span></span>
<span data-ttu-id="336ab-102">Určuje adresu a vazbu místního vystavitele, který se má použít k získání tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="336ab-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="336ab-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="336ab-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="336ab-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="336ab-104">\<behaviors></span></span>  
<span data-ttu-id="336ab-105">oddíl endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="336ab-105">endpointBehaviors section</span></span>  
<span data-ttu-id="336ab-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="336ab-106">\<behavior></span></span>  
<span data-ttu-id="336ab-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="336ab-107">\<clientCredentials></span></span>  
<span data-ttu-id="336ab-108">\<Třídy IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="336ab-108">\<issuedToken></span></span>  
<span data-ttu-id="336ab-109">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="336ab-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="336ab-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="336ab-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="336ab-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="336ab-111">Attributes and Elements</span></span>  
 <span data-ttu-id="336ab-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="336ab-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="336ab-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="336ab-113">Attributes</span></span>  
  
|<span data-ttu-id="336ab-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="336ab-114">Attribute</span></span>|<span data-ttu-id="336ab-115">Popis</span><span class="sxs-lookup"><span data-stu-id="336ab-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="336ab-116">adresa</span><span class="sxs-lookup"><span data-stu-id="336ab-116">address</span></span>|<span data-ttu-id="336ab-117">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="336ab-117">Required string.</span></span> <span data-ttu-id="336ab-118">Určuje identifikátor URI místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="336ab-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="336ab-119">vazba</span><span class="sxs-lookup"><span data-stu-id="336ab-119">binding</span></span>|<span data-ttu-id="336ab-120">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="336ab-120">Optional string.</span></span> <span data-ttu-id="336ab-121">Jedna z vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="336ab-121">One of the system-provided bindings.</span></span> <span data-ttu-id="336ab-122">Seznam najdete v tématu [vazby poskytované systémem](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="336ab-122">For a list, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="336ab-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="336ab-123">bindingConfiguration</span></span>|<span data-ttu-id="336ab-124">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="336ab-124">Optional string.</span></span> <span data-ttu-id="336ab-125">Určuje konfiguraci vazby nalezenou v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="336ab-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="336ab-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="336ab-126">Child Elements</span></span>  
  
|<span data-ttu-id="336ab-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="336ab-127">Element</span></span>|<span data-ttu-id="336ab-128">Popis</span><span class="sxs-lookup"><span data-stu-id="336ab-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="336ab-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="336ab-129">\<identity></span></span>](identity.md)|<span data-ttu-id="336ab-130">Určuje informace o identitě místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="336ab-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="336ab-131">\<headers></span><span class="sxs-lookup"><span data-stu-id="336ab-131">\<headers></span></span>](headers-element.md)|<span data-ttu-id="336ab-132">Kolekce hlaviček adres, které jsou požadovány pro správné adresování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="336ab-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="336ab-133">K přidání záhlaví do `add` této kolekce můžete použít klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="336ab-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="336ab-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="336ab-134">Parent Elements</span></span>  
  
|<span data-ttu-id="336ab-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="336ab-135">Element</span></span>|<span data-ttu-id="336ab-136">Popis</span><span class="sxs-lookup"><span data-stu-id="336ab-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="336ab-137">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="336ab-137">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="336ab-138">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="336ab-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="336ab-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="336ab-139">Remarks</span></span>  
 <span data-ttu-id="336ab-140">Při získávání vystaveného tokenu ze služby tokenu zabezpečení (STS) musí být klientská aplikace nakonfigurovaná s adresou a vazbou, která se má použít ke komunikaci se službou STS.</span><span class="sxs-lookup"><span data-stu-id="336ab-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="336ab-141">Pokud neposkytuje adresu URL pro službu tokenu zabezpečení, nebo pokud je `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` adresa vystavitele federované vazby nebo `null`, kanál Windows Communication Foundation (WCF) klienta používá hodnoty určené parametrem <xref:System.ServiceModel.WSFederationHttpBinding> `address` a`binding` ke komunikaci se službou STS pro získání vydaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="336ab-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="336ab-142">Další informace o konfiguraci místního vystavitele najdete v [tématu Postup: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="336ab-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="336ab-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="336ab-143">Example</span></span>  
 <span data-ttu-id="336ab-144">V následujícím příkladu jsou nastaveny `address`atributy `binding` `bindingConfiguration` , a elementu. `localIssuer`</span><span class="sxs-lookup"><span data-stu-id="336ab-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="MyEndpointBehavior">
        <clientCredentials>
          <issuedToken cacheIssuedTokens="false"
                       defaultKeyEntropyMode="ClientEntropy">
            <localIssuer address="net.tcp://cohowinery/tokens"
                         binding="netTcpBinding"
                         bindingConfiguration="myTcpBindingConfig" />
          </issuedToken>
        </clientCredentials>
      </behavior>
    </endpointBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="336ab-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="336ab-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="336ab-146">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="336ab-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="336ab-147">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="336ab-147">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="336ab-148">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="336ab-148">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="336ab-149">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="336ab-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="336ab-150">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="336ab-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="336ab-151">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="336ab-151">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="336ab-152">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="336ab-152">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="336ab-153">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="336ab-153">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="336ab-154">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="336ab-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
