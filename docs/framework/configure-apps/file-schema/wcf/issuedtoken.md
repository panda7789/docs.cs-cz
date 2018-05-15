---
title: '&lt;IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 9a8d701e0806aae0a17a1c5ff7284606dd080f85
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuedtokengt"></a><span data-ttu-id="0e797-102">&lt;IssuedToken&gt;</span><span class="sxs-lookup"><span data-stu-id="0e797-102">&lt;issuedToken&gt;</span></span>
<span data-ttu-id="0e797-103">Určuje vlastní token používaný k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="0e797-103">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="0e797-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0e797-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0e797-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0e797-105">\<behaviors></span></span>  
<span data-ttu-id="0e797-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="0e797-106">endpointBehaviors section</span></span>  
<span data-ttu-id="0e797-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="0e797-107">\<behavior></span></span>  
<span data-ttu-id="0e797-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="0e797-108">\<clientCredentials></span></span>  
<span data-ttu-id="0e797-109">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="0e797-109">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e797-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e797-110">Syntax</span></span>  
  
```xml  
<issuedToken   
   cacheIssuedTokens="Boolean"  
   defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"  
   issuedTokenRenewalThresholdPercentage = "0 to 100"  
   issuerChannelBehaviors="String"  
      localIssuerChannelBehaviors="String"  
   maxIssuedTokenCachingTime="TimeSpan"  
</issuedToken>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e797-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0e797-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0e797-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0e797-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e797-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="0e797-113">Attributes</span></span>  
  
|<span data-ttu-id="0e797-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="0e797-114">Attribute</span></span>|<span data-ttu-id="0e797-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0e797-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="0e797-116">Volitelný logický atribut, který určuje, zda jsou do mezipaměti tokenů.</span><span class="sxs-lookup"><span data-stu-id="0e797-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="0e797-117">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="0e797-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="0e797-118">Volitelný řetězec atribut, který určuje, které náhodných hodnot (entropies) se používá pro operace metody handshake.</span><span class="sxs-lookup"><span data-stu-id="0e797-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="0e797-119">Hodnoty zahrnují `ClientEntropy`, `ServerEntropy`, a `CombinedEntropy`, výchozí hodnota je `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="0e797-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="0e797-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="0e797-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="0e797-121">Volitelné číslo atribut, který určuje procento platný časovém rámci (poskytl vydavatel tokenu), může uplynout, než token byl obnoven.</span><span class="sxs-lookup"><span data-stu-id="0e797-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="0e797-122">Hodnoty jsou od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="0e797-122">Values are from 0 to 100.</span></span> <span data-ttu-id="0e797-123">Výchozí hodnota je 60, který určuje 60 % doby přerušeno dříve, než dojde k pokusu o obnovení.</span><span class="sxs-lookup"><span data-stu-id="0e797-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="0e797-124">Volitelný atribut, který určuje chování kanál používat při komunikaci s vystavitele.</span><span class="sxs-lookup"><span data-stu-id="0e797-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="0e797-125">Volitelný atribut, který určuje chování kanál používat při komunikaci s místní vystavitele.</span><span class="sxs-lookup"><span data-stu-id="0e797-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="0e797-126">Volitelný atribut časový interval, který určuje dobu, která vydala tokeny jsou uložené v mezipaměti při vydavatel tokenu (služby tokenů zabezpečení) neurčuje čas.</span><span class="sxs-lookup"><span data-stu-id="0e797-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="0e797-127">Výchozí hodnota je "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="0e797-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e797-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0e797-128">Child Elements</span></span>  
  
|<span data-ttu-id="0e797-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e797-129">Element</span></span>|<span data-ttu-id="0e797-130">Popis</span><span class="sxs-lookup"><span data-stu-id="0e797-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e797-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="0e797-131">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="0e797-132">Určuje adresu místního vystavitele tokenu a vazby používaný ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="0e797-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="0e797-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0e797-133">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="0e797-134">Určuje chování koncový bod při kontaktování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="0e797-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e797-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0e797-135">Parent Elements</span></span>  
  
|<span data-ttu-id="0e797-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e797-136">Element</span></span>|<span data-ttu-id="0e797-137">Popis</span><span class="sxs-lookup"><span data-stu-id="0e797-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e797-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="0e797-138">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="0e797-139">Určuje pověření použitá k ověření klienta pro službu.</span><span class="sxs-lookup"><span data-stu-id="0e797-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e797-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e797-140">Remarks</span></span>  
 <span data-ttu-id="0e797-141">Vystavený token je typu vlastní pověření, použije, například při ověřování s zabezpečení tokenu služby (STS) v případě federovaných.</span><span class="sxs-lookup"><span data-stu-id="0e797-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="0e797-142">Ve výchozím nastavení je token SAML token.</span><span class="sxs-lookup"><span data-stu-id="0e797-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="0e797-143">Další informace najdete v tématu [federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="0e797-143">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="0e797-144">a [federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="0e797-144">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="0e797-145">Tato část obsahuje prvky, které konfigurace místního vystavitele tokeny nebo chování použít s služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0e797-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="0e797-146">Pokyny týkající se konfigurace klienta pomocí místního vystavitele najdete v tématu [postupy: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="0e797-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e797-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e797-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="0e797-148">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0e797-148">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="0e797-149">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0e797-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="0e797-150">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="0e797-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="0e797-151">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="0e797-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="0e797-152">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="0e797-152">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="0e797-153">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="0e797-153">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="0e797-154">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="0e797-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
