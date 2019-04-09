---
title: <localIssuer>
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 9a51387cd75d57a6828ecde1dcd788b056f7e27a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122873"
---
# <a name="localissuer"></a><span data-ttu-id="872b1-101">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="872b1-101">\<localIssuer></span></span>
<span data-ttu-id="872b1-102">Určuje adresu a vazbu lokálního vystavitele, který se má použít k získání tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="872b1-102">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="872b1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="872b1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="872b1-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="872b1-104">\<behaviors></span></span>  
<span data-ttu-id="872b1-105">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="872b1-105">endpointBehaviors section</span></span>  
<span data-ttu-id="872b1-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="872b1-106">\<behavior></span></span>  
<span data-ttu-id="872b1-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="872b1-107">\<clientCredentials></span></span>  
<span data-ttu-id="872b1-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="872b1-108">\<issuedToken></span></span>  
<span data-ttu-id="872b1-109">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="872b1-109">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="872b1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="872b1-110">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="872b1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="872b1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="872b1-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="872b1-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="872b1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="872b1-113">Attributes</span></span>  
  
|<span data-ttu-id="872b1-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="872b1-114">Attribute</span></span>|<span data-ttu-id="872b1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="872b1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="872b1-116">adresa</span><span class="sxs-lookup"><span data-stu-id="872b1-116">address</span></span>|<span data-ttu-id="872b1-117">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="872b1-117">Required string.</span></span> <span data-ttu-id="872b1-118">Určuje identifikátor URI místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="872b1-118">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="872b1-119">vazba</span><span class="sxs-lookup"><span data-stu-id="872b1-119">binding</span></span>|<span data-ttu-id="872b1-120">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="872b1-120">Optional string.</span></span> <span data-ttu-id="872b1-121">Jedna z vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="872b1-121">One of the system-provided bindings.</span></span> <span data-ttu-id="872b1-122">Seznam najdete v tématu [System-Provided vazby](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="872b1-122">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="872b1-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="872b1-123">bindingConfiguration</span></span>|<span data-ttu-id="872b1-124">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="872b1-124">Optional string.</span></span> <span data-ttu-id="872b1-125">Určuje konfiguraci vazby nacházející se v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="872b1-125">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="872b1-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="872b1-126">Child Elements</span></span>  
  
|<span data-ttu-id="872b1-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="872b1-127">Element</span></span>|<span data-ttu-id="872b1-128">Popis</span><span class="sxs-lookup"><span data-stu-id="872b1-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="872b1-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="872b1-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="872b1-130">Určuje informace o identitě pro lokálního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="872b1-130">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="872b1-131">\<headers></span><span class="sxs-lookup"><span data-stu-id="872b1-131">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="872b1-132">Kolekce záhlaví adres nutných ke správnému adresování lokálního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="872b1-132">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="872b1-133">Můžete použít `add` – klíčové slovo do této kolekce přidat hlavičku.</span><span class="sxs-lookup"><span data-stu-id="872b1-133">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="872b1-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="872b1-134">Parent Elements</span></span>  
  
|<span data-ttu-id="872b1-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="872b1-135">Element</span></span>|<span data-ttu-id="872b1-136">Popis</span><span class="sxs-lookup"><span data-stu-id="872b1-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="872b1-137">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="872b1-137">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="872b1-138">Určuje vlastní token pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="872b1-138">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="872b1-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="872b1-139">Remarks</span></span>  
 <span data-ttu-id="872b1-140">Při získávání vydaný token z tokenu služby zabezpečení (STS), klientská aplikace musí být nakonfigurované s adresou a vazba k použití pro komunikaci pomocí služby STS.</span><span class="sxs-lookup"><span data-stu-id="872b1-140">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="872b1-141">Když <xref:System.ServiceModel.WSFederationHttpBinding> neposkytuje adresu URL pro službu tokenů zabezpečení, nebo když je adresa vystavitele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null`, kanálu klienta Windows Communication Foundation (WCF) používá hodnoty zadané ve `address`a `binding` ke komunikaci s služby STS pro získání vydaný token.</span><span class="sxs-lookup"><span data-stu-id="872b1-141">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="872b1-142">Další informace týkající se konfigurace místního vystavitele najdete v tématu [jak: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="872b1-142">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="872b1-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="872b1-143">Example</span></span>  
 <span data-ttu-id="872b1-144">Následující příklad nastaví `address`, `binding`, a `bindingConfiguration` atributy `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="872b1-144">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="872b1-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="872b1-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="872b1-146">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="872b1-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="872b1-147">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="872b1-147">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="872b1-148">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="872b1-148">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="872b1-149">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="872b1-149">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="872b1-150">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="872b1-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="872b1-151">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="872b1-151">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="872b1-152">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="872b1-152">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="872b1-153">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="872b1-153">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="872b1-154">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="872b1-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
