---
title: '&lt;localIssuer&gt;'
ms.date: 03/30/2017
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
ms.openlocfilehash: 7a48cbb3a1e17ac1fc9fa9f43301ef153cdb866c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151867"
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="9df22-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="9df22-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="9df22-103">Určuje adresu a vazbu lokálního vystavitele, který se má použít k získání tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9df22-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="9df22-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9df22-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9df22-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9df22-105">\<behaviors></span></span>  
<span data-ttu-id="9df22-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="9df22-106">endpointBehaviors section</span></span>  
<span data-ttu-id="9df22-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9df22-107">\<behavior></span></span>  
<span data-ttu-id="9df22-108">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="9df22-108">\<clientCredentials></span></span>  
<span data-ttu-id="9df22-109">\<třídy issuedToken ></span><span class="sxs-lookup"><span data-stu-id="9df22-109">\<issuedToken></span></span>  
<span data-ttu-id="9df22-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="9df22-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df22-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9df22-111">Syntax</span></span>  
  
```xml  
<localIssuer address="String"
             binding="String"
             bindingConfiguration="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9df22-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9df22-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9df22-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9df22-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9df22-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="9df22-114">Attributes</span></span>  
  
|<span data-ttu-id="9df22-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="9df22-115">Attribute</span></span>|<span data-ttu-id="9df22-116">Popis</span><span class="sxs-lookup"><span data-stu-id="9df22-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9df22-117">adresa</span><span class="sxs-lookup"><span data-stu-id="9df22-117">address</span></span>|<span data-ttu-id="9df22-118">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="9df22-118">Required string.</span></span> <span data-ttu-id="9df22-119">Určuje identifikátor URI místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="9df22-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="9df22-120">vazba</span><span class="sxs-lookup"><span data-stu-id="9df22-120">binding</span></span>|<span data-ttu-id="9df22-121">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="9df22-121">Optional string.</span></span> <span data-ttu-id="9df22-122">Jedna z vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="9df22-122">One of the system-provided bindings.</span></span> <span data-ttu-id="9df22-123">Seznam najdete v tématu [System-Provided vazby](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="9df22-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="9df22-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="9df22-124">bindingConfiguration</span></span>|<span data-ttu-id="9df22-125">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="9df22-125">Optional string.</span></span> <span data-ttu-id="9df22-126">Určuje konfiguraci vazby nacházející se v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="9df22-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9df22-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9df22-127">Child Elements</span></span>  
  
|<span data-ttu-id="9df22-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="9df22-128">Element</span></span>|<span data-ttu-id="9df22-129">Popis</span><span class="sxs-lookup"><span data-stu-id="9df22-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9df22-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="9df22-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="9df22-131">Určuje informace o identitě pro lokálního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="9df22-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="9df22-132">\<záhlaví ></span><span class="sxs-lookup"><span data-stu-id="9df22-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="9df22-133">Kolekce záhlaví adres nutných ke správnému adresování lokálního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="9df22-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="9df22-134">Můžete použít `add` – klíčové slovo do této kolekce přidat hlavičku.</span><span class="sxs-lookup"><span data-stu-id="9df22-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9df22-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9df22-135">Parent Elements</span></span>  
  
|<span data-ttu-id="9df22-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="9df22-136">Element</span></span>|<span data-ttu-id="9df22-137">Popis</span><span class="sxs-lookup"><span data-stu-id="9df22-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9df22-138">\<třídy issuedToken ></span><span class="sxs-lookup"><span data-stu-id="9df22-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="9df22-139">Určuje vlastní token pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="9df22-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9df22-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9df22-140">Remarks</span></span>  
 <span data-ttu-id="9df22-141">Při získávání vydaný token z tokenu služby zabezpečení (STS), klientská aplikace musí být nakonfigurované s adresou a vazba k použití pro komunikaci pomocí služby STS.</span><span class="sxs-lookup"><span data-stu-id="9df22-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="9df22-142">Když <xref:System.ServiceModel.WSFederationHttpBinding> neposkytuje adresu URL pro službu tokenů zabezpečení, nebo když je adresa vystavitele federované vazby `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` nebo `null`, kanálu klienta Windows Communication Foundation (WCF) používá hodnoty zadané ve `address`a `binding` ke komunikaci s služby STS pro získání vydaný token.</span><span class="sxs-lookup"><span data-stu-id="9df22-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`, the client's Windows Communication Foundation (WCF) channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="9df22-143">Další informace týkající se konfigurace místního vystavitele najdete v tématu [jak: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="9df22-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9df22-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="9df22-144">Example</span></span>  
 <span data-ttu-id="9df22-145">Následující příklad nastaví `address`, `binding`, a `bindingConfiguration` atributy `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="9df22-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9df22-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="9df22-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="9df22-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9df22-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="9df22-148">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="9df22-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="9df22-149">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="9df22-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="9df22-150">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9df22-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="9df22-151">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="9df22-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="9df22-152">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9df22-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="9df22-153">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="9df22-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="9df22-154">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="9df22-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="9df22-155">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="9df22-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
