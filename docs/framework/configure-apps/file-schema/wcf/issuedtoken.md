---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: a70c694509cd35e9bff7d56ae278da93b9b2b9ce
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273030"
---
# <a name="issuedtoken"></a><span data-ttu-id="fa27e-101">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="fa27e-101">\<issuedToken></span></span>
<span data-ttu-id="fa27e-102">Určuje vlastní token pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="fa27e-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="fa27e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fa27e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa27e-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fa27e-104">\<behaviors></span></span>  
<span data-ttu-id="fa27e-105">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="fa27e-105">endpointBehaviors section</span></span>  
<span data-ttu-id="fa27e-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="fa27e-106">\<behavior></span></span>  
<span data-ttu-id="fa27e-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="fa27e-107">\<clientCredentials></span></span>  
<span data-ttu-id="fa27e-108">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="fa27e-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa27e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa27e-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa27e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fa27e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fa27e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fa27e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa27e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="fa27e-112">Attributes</span></span>  
  
|<span data-ttu-id="fa27e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="fa27e-113">Attribute</span></span>|<span data-ttu-id="fa27e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fa27e-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="fa27e-115">Volitelný logický atribut, který určuje, zda tokeny uchovávány v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="fa27e-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="fa27e-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="fa27e-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="fa27e-117">Volitelný atribut řetězce, který určuje náhodné hodnoty (entropies) se používají pro metodu handshake.</span><span class="sxs-lookup"><span data-stu-id="fa27e-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="fa27e-118">Mezi hodnoty patří `ClientEntropy`, `ServerEntropy`, a `CombinedEntropy`, výchozí hodnota je `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="fa27e-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="fa27e-119">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="fa27e-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="fa27e-120">Volitelný celočíselný atribut, který určuje procento platných období (poskytnutých vystavitelem tokenu), která mohou uplynout před obnovením tokenu.</span><span class="sxs-lookup"><span data-stu-id="fa27e-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="fa27e-121">Hodnoty jsou od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="fa27e-121">Values are from 0 to 100.</span></span> <span data-ttu-id="fa27e-122">Výchozí hodnota je 60, který určuje 60 % časových intervalech, než dojde k pokusu o obnovení.</span><span class="sxs-lookup"><span data-stu-id="fa27e-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="fa27e-123">Volitelný atribut, který určuje chování kanálu při komunikaci s vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="fa27e-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="fa27e-124">Volitelný atribut, který určuje chování kanálu při komunikaci s místním vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="fa27e-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="fa27e-125">Volitelný atribut Timespan, který určuje dobu, po kterou jsou vydané tokeny ukládány do mezipaměti, když vystavitel (STS) neurčuje čas.</span><span class="sxs-lookup"><span data-stu-id="fa27e-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="fa27e-126">Výchozí hodnota je "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="fa27e-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa27e-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fa27e-127">Child Elements</span></span>  
  
|<span data-ttu-id="fa27e-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="fa27e-128">Element</span></span>|<span data-ttu-id="fa27e-129">Popis</span><span class="sxs-lookup"><span data-stu-id="fa27e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa27e-130">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="fa27e-130">\<localIssuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)|<span data-ttu-id="fa27e-131">Určuje adresu místního vystavitele tokenu a vazby používaný ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="fa27e-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="fa27e-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="fa27e-132">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="fa27e-133">Určuje chování koncového bodu při kontaktování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="fa27e-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa27e-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fa27e-134">Parent Elements</span></span>  
  
|<span data-ttu-id="fa27e-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="fa27e-135">Element</span></span>|<span data-ttu-id="fa27e-136">Popis</span><span class="sxs-lookup"><span data-stu-id="fa27e-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa27e-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="fa27e-137">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="fa27e-138">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="fa27e-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa27e-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa27e-139">Remarks</span></span>  
 <span data-ttu-id="fa27e-140">Vydaný token má typ vlastní pověření, například používaný při ověřování s zabezpečení tokenu služby (STS) ve scénáři federované.</span><span class="sxs-lookup"><span data-stu-id="fa27e-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="fa27e-141">Ve výchozím nastavení token je SAML token.</span><span class="sxs-lookup"><span data-stu-id="fa27e-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="fa27e-142">Další informace najdete v tématu [federace a vydané tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="fa27e-142">For more information, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="fa27e-143">a [federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="fa27e-143">and [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="fa27e-144">Tato část obsahuje prvků, které slouží ke konfiguraci místního vystavitele tokeny nebo chování používaná službou tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fa27e-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="fa27e-145">Pokyny ke konfiguraci klienta pro použití místního vystavitele, naleznete v tématu [jak: Konfigurace místního vystavitele](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="fa27e-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa27e-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa27e-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="fa27e-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fa27e-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="fa27e-148">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fa27e-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fa27e-149">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="fa27e-149">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="fa27e-150">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="fa27e-150">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="fa27e-151">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="fa27e-151">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="fa27e-152">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="fa27e-152">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="fa27e-153">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="fa27e-153">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
