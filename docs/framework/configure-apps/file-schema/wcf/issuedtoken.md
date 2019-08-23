---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 68e3a0802a10b14148188a81ee24ed901caa147f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925384"
---
# <a name="issuedtoken"></a><span data-ttu-id="246c6-101">\<Třídy IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="246c6-101">\<issuedToken></span></span>
<span data-ttu-id="246c6-102">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="246c6-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
 <span data-ttu-id="246c6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="246c6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="246c6-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="246c6-104">\<behaviors></span></span>  
<span data-ttu-id="246c6-105">oddíl endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="246c6-105">endpointBehaviors section</span></span>  
<span data-ttu-id="246c6-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="246c6-106">\<behavior></span></span>  
<span data-ttu-id="246c6-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="246c6-107">\<clientCredentials></span></span>  
<span data-ttu-id="246c6-108">\<Třídy IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="246c6-108">\<issuedToken></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="246c6-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="246c6-109">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="246c6-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="246c6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="246c6-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="246c6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="246c6-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="246c6-112">Attributes</span></span>  
  
|<span data-ttu-id="246c6-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="246c6-113">Attribute</span></span>|<span data-ttu-id="246c6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="246c6-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="246c6-115">Volitelný logický atribut, který určuje, zda jsou tokeny uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="246c6-115">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="246c6-116">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="246c6-116">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="246c6-117">Volitelný řetězcový atribut určující, které náhodné hodnoty (jenž) se používají pro operace handshake.</span><span class="sxs-lookup"><span data-stu-id="246c6-117">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="246c6-118">Mezi hodnoty `ClientEntropy`patří `ServerEntropy`, a `CombinedEntropy`. výchozí hodnota je `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="246c6-118">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="246c6-119">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="246c6-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="246c6-120">Volitelný celočíselný atribut, který určuje procentuální hodnotu platného časového rámce (poskytnutý vystavitelem tokenu), který může uplynout před obnovením tokenu.</span><span class="sxs-lookup"><span data-stu-id="246c6-120">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="246c6-121">Hodnoty jsou od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="246c6-121">Values are from 0 to 100.</span></span> <span data-ttu-id="246c6-122">Výchozí hodnota je 60, která určuje 60% času průchodu před pokusem o obnovení.</span><span class="sxs-lookup"><span data-stu-id="246c6-122">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="246c6-123">Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="246c6-123">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="246c6-124">Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s místním vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="246c6-124">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="246c6-125">Volitelný atribut TimeSpan, který určuje dobu, po kterou jsou vydané tokeny ukládány do mezipaměti v případě, že Vystavitel tokenů (STS) neurčuje čas.</span><span class="sxs-lookup"><span data-stu-id="246c6-125">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="246c6-126">Výchozí hodnota je "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="246c6-126">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="246c6-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="246c6-127">Child Elements</span></span>  
  
|<span data-ttu-id="246c6-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="246c6-128">Element</span></span>|<span data-ttu-id="246c6-129">Popis</span><span class="sxs-lookup"><span data-stu-id="246c6-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="246c6-130">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="246c6-130">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="246c6-131">Určuje adresu místního vystavitele tokenu a vazbu, která se používá ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="246c6-131">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="246c6-132">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="246c6-132">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="246c6-133">Určuje chování koncového bodu, které se má použít při kontaktování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="246c6-133">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="246c6-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="246c6-134">Parent Elements</span></span>  
  
|<span data-ttu-id="246c6-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="246c6-135">Element</span></span>|<span data-ttu-id="246c6-136">Popis</span><span class="sxs-lookup"><span data-stu-id="246c6-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="246c6-137">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="246c6-137">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="246c6-138">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="246c6-138">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="246c6-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="246c6-139">Remarks</span></span>  
 <span data-ttu-id="246c6-140">Vydaný token je vlastní typ přihlašovacích údajů, který se používá například při ověřování pomocí služby tokenů zabezpečení (STS) ve federovaném scénáři.</span><span class="sxs-lookup"><span data-stu-id="246c6-140">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="246c6-141">Ve výchozím nastavení je tokenem token SAML.</span><span class="sxs-lookup"><span data-stu-id="246c6-141">By default, the token is a SAML token.</span></span> <span data-ttu-id="246c6-142">Další informace najdete v tématu [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="246c6-142">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="246c6-143">a [federačních a](../../../wcf/feature-details/federation-and-issued-tokens.md)vydaných tokenů.</span><span class="sxs-lookup"><span data-stu-id="246c6-143">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="246c6-144">Tato část obsahuje prvky, které slouží ke konfiguraci místního vystavitele tokenů nebo chování používaného se službou tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="246c6-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="246c6-145">Pokyny ke konfiguraci klienta pro použití místního vystavitele najdete v tématu [How to: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="246c6-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="246c6-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="246c6-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="246c6-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="246c6-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="246c6-148">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="246c6-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="246c6-149">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="246c6-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="246c6-150">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="246c6-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="246c6-151">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="246c6-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="246c6-152">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="246c6-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="246c6-153">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="246c6-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
