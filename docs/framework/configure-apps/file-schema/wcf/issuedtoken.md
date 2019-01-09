---
title: '&lt;Třídy IssuedToken&gt;'
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: a06d59c5dfb14e5f3346ff2424339659568a369a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150185"
---
# <a name="ltissuedtokengt"></a><span data-ttu-id="bed73-102">&lt;Třídy IssuedToken&gt;</span><span class="sxs-lookup"><span data-stu-id="bed73-102">&lt;issuedToken&gt;</span></span>
<span data-ttu-id="bed73-103">Určuje vlastní token pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="bed73-103">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="bed73-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bed73-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bed73-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bed73-105">\<behaviors></span></span>  
<span data-ttu-id="bed73-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="bed73-106">endpointBehaviors section</span></span>  
<span data-ttu-id="bed73-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bed73-107">\<behavior></span></span>  
<span data-ttu-id="bed73-108">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="bed73-108">\<clientCredentials></span></span>  
<span data-ttu-id="bed73-109">\<třídy issuedToken ></span><span class="sxs-lookup"><span data-stu-id="bed73-109">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed73-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bed73-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bed73-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bed73-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bed73-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bed73-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bed73-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="bed73-113">Attributes</span></span>  
  
|<span data-ttu-id="bed73-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="bed73-114">Attribute</span></span>|<span data-ttu-id="bed73-115">Popis</span><span class="sxs-lookup"><span data-stu-id="bed73-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="bed73-116">Volitelný logický atribut, který určuje, zda tokeny uchovávány v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="bed73-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="bed73-117">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="bed73-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="bed73-118">Volitelný atribut řetězce, který určuje náhodné hodnoty (entropies) se používají pro metodu handshake.</span><span class="sxs-lookup"><span data-stu-id="bed73-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="bed73-119">Mezi hodnoty patří `ClientEntropy`, `ServerEntropy`, a `CombinedEntropy`, výchozí hodnota je `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="bed73-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="bed73-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="bed73-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="bed73-121">Volitelný celočíselný atribut, který určuje procento platných období (poskytnutých vystavitelem tokenu), která mohou uplynout před obnovením tokenu.</span><span class="sxs-lookup"><span data-stu-id="bed73-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="bed73-122">Hodnoty jsou od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="bed73-122">Values are from 0 to 100.</span></span> <span data-ttu-id="bed73-123">Výchozí hodnota je 60, který určuje 60 % časových intervalech, než dojde k pokusu o obnovení.</span><span class="sxs-lookup"><span data-stu-id="bed73-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="bed73-124">Volitelný atribut, který určuje chování kanálu při komunikaci s vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="bed73-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="bed73-125">Volitelný atribut, který určuje chování kanálu při komunikaci s místním vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="bed73-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="bed73-126">Volitelný atribut Timespan, který určuje dobu, po kterou jsou vydané tokeny ukládány do mezipaměti, když vystavitel (STS) neurčuje čas.</span><span class="sxs-lookup"><span data-stu-id="bed73-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="bed73-127">Výchozí hodnota je "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="bed73-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bed73-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bed73-128">Child Elements</span></span>  
  
|<span data-ttu-id="bed73-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="bed73-129">Element</span></span>|<span data-ttu-id="bed73-130">Popis</span><span class="sxs-lookup"><span data-stu-id="bed73-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bed73-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="bed73-131">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="bed73-132">Určuje adresu místního vystavitele tokenu a vazby používaný ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="bed73-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="bed73-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bed73-133">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="bed73-134">Určuje chování koncového bodu při kontaktování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="bed73-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bed73-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bed73-135">Parent Elements</span></span>  
  
|<span data-ttu-id="bed73-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="bed73-136">Element</span></span>|<span data-ttu-id="bed73-137">Popis</span><span class="sxs-lookup"><span data-stu-id="bed73-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bed73-138">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="bed73-138">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="bed73-139">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="bed73-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bed73-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bed73-140">Remarks</span></span>  
 <span data-ttu-id="bed73-141">Vydaný token má typ vlastní pověření, například používaný při ověřování s zabezpečení tokenu služby (STS) ve scénáři federované.</span><span class="sxs-lookup"><span data-stu-id="bed73-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="bed73-142">Ve výchozím nastavení token je SAML token.</span><span class="sxs-lookup"><span data-stu-id="bed73-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="bed73-143">Další informace najdete v tématu [federace a vydané tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="bed73-143">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="bed73-144">a [federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="bed73-144">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="bed73-145">Tato část obsahuje prvků, které slouží ke konfiguraci místního vystavitele tokeny nebo chování používaná službou tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bed73-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="bed73-146">Pokyny ke konfiguraci klienta pro použití místního vystavitele, naleznete v tématu [jak: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="bed73-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed73-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="bed73-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
 [<span data-ttu-id="bed73-148">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bed73-148">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="bed73-149">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bed73-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="bed73-150">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="bed73-150">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="bed73-151">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="bed73-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="bed73-152">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="bed73-152">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="bed73-153">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="bed73-153">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="bed73-154">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="bed73-154">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
