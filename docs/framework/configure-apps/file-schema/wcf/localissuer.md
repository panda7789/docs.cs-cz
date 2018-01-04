---
title: '&lt;localIssuer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26bdd0df-0e7d-4b9e-bbeb-f28c53769385
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c7e5c28325326d838da851ff4add12f8ae612c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltlocalissuergt"></a><span data-ttu-id="5455c-102">&lt;localIssuer&gt;</span><span class="sxs-lookup"><span data-stu-id="5455c-102">&lt;localIssuer&gt;</span></span>
<span data-ttu-id="5455c-103">Určuje adresu a vazba místního vystavitele, který se má použít k získání tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5455c-103">Specifies the address and binding of the local issuer to be used to obtain a security token.</span></span>  
  
 <span data-ttu-id="5455c-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5455c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5455c-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5455c-105">\<behaviors></span></span>  
<span data-ttu-id="5455c-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="5455c-106">endpointBehaviors section</span></span>  
<span data-ttu-id="5455c-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5455c-107">\<behavior></span></span>  
<span data-ttu-id="5455c-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5455c-108">\<clientCredentials></span></span>  
<span data-ttu-id="5455c-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="5455c-109">\<issuedToken></span></span>  
<span data-ttu-id="5455c-110">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="5455c-110">\<localIssuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5455c-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5455c-111">Syntax</span></span>  
  
```xml  
<localIssuer address="string"  
      binding="string"  
      bindingConfiguration="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5455c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5455c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5455c-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5455c-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5455c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5455c-114">Attributes</span></span>  
  
|<span data-ttu-id="5455c-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="5455c-115">Attribute</span></span>|<span data-ttu-id="5455c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5455c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5455c-117">adresa</span><span class="sxs-lookup"><span data-stu-id="5455c-117">address</span></span>|<span data-ttu-id="5455c-118">Požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5455c-118">Required string.</span></span> <span data-ttu-id="5455c-119">Určuje identifikátor URI místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="5455c-119">Specifies the URI of the local issuer.</span></span>|  
|<span data-ttu-id="5455c-120">vazba</span><span class="sxs-lookup"><span data-stu-id="5455c-120">binding</span></span>|<span data-ttu-id="5455c-121">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5455c-121">Optional string.</span></span> <span data-ttu-id="5455c-122">Jeden z vazby poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="5455c-122">One of the system-provided bindings.</span></span> <span data-ttu-id="5455c-123">Seznam najdete v tématu [System-Provided vazby](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="5455c-123">For a list, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>|  
|<span data-ttu-id="5455c-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="5455c-124">bindingConfiguration</span></span>|<span data-ttu-id="5455c-125">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5455c-125">Optional string.</span></span> <span data-ttu-id="5455c-126">Určuje konfiguraci vazby v konfiguračním souboru nalézt.</span><span class="sxs-lookup"><span data-stu-id="5455c-126">Specifies a binding configuration found in the configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5455c-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5455c-127">Child Elements</span></span>  
  
|<span data-ttu-id="5455c-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="5455c-128">Element</span></span>|<span data-ttu-id="5455c-129">Popis</span><span class="sxs-lookup"><span data-stu-id="5455c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5455c-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="5455c-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="5455c-131">Určuje informace o identitě pro místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="5455c-131">Specifies identity information for the local issuer.</span></span>|  
|[<span data-ttu-id="5455c-132">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="5455c-132">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="5455c-133">Kolekce hlavičky adresy, které jsou požadovány k správně adres místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="5455c-133">A collection of address headers that are required in order to correctly address the local issuer.</span></span> <span data-ttu-id="5455c-134">Můžete použít `add` – klíčové slovo přidat hlavičku do této kolekce.</span><span class="sxs-lookup"><span data-stu-id="5455c-134">You can use the `add` keyword to add a header to this collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5455c-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5455c-135">Parent Elements</span></span>  
  
|<span data-ttu-id="5455c-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="5455c-136">Element</span></span>|<span data-ttu-id="5455c-137">Popis</span><span class="sxs-lookup"><span data-stu-id="5455c-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5455c-138">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="5455c-138">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="5455c-139">Určuje vlastní token používaný k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="5455c-139">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5455c-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5455c-140">Remarks</span></span>  
 <span data-ttu-id="5455c-141">Při získávání tokenu vydaných z zabezpečení tokenu služby (STS), klient aplikace musí být nakonfigurována s adresou a vazbou, který bude používat pro komunikaci se služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5455c-141">When obtaining an issued token from a Security Token Service (STS), the client application must be configured with the address and binding to use to communicate with the STS.</span></span> <span data-ttu-id="5455c-142">Když <xref:System.ServiceModel.WSFederationHttpBinding> neposkytuje adresu URL pro službu tokenů zabezpečení, nebo když adresa vystavitele federované vazby je http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous nebo `null`, klienta [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] kanál používá hodnoty zadané ve `address` a `binding` ke komunikaci s služby tokenů zabezpečení získat vydaný token.</span><span class="sxs-lookup"><span data-stu-id="5455c-142">When the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous or `null`, the client's [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] channel uses the values specified by `address` and `binding` to communicate with the STS to obtain the issued token.</span></span> <span data-ttu-id="5455c-143">Další informace týkající se konfigurace místního vystavitele najdete v tématu [postupy: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="5455c-143">For more information on configuring a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5455c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="5455c-144">Example</span></span>  
 <span data-ttu-id="5455c-145">Následující příklad nastavuje `address`, `binding`, a `bindingConfiguration` atributy `localIssuer` elementu.</span><span class="sxs-lookup"><span data-stu-id="5455c-145">The following example sets the `address`, `binding`, and `bindingConfiguration` attributes of a `localIssuer` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5455c-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="5455c-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.LocalIssuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="5455c-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5455c-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="5455c-148">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="5455c-148">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="5455c-149">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="5455c-149">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5455c-150">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5455c-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="5455c-151">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="5455c-151">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="5455c-152">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5455c-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5455c-153">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="5455c-153">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="5455c-154">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="5455c-154">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="5455c-155">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="5455c-155">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
