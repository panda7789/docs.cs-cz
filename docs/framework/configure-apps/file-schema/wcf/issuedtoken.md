---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846863"
---
# <a name="issuedtoken"></a><span data-ttu-id="89ce5-101">\<třídy IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="89ce5-101">\<issuedToken></span></span>
<span data-ttu-id="89ce5-102">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="89ce5-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="89ce5-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="89ce5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="89ce5-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="89ce5-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="89ce5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**chování**](behaviors.md)\<</span><span class="sxs-lookup"><span data-stu-id="89ce5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\</span></span>
<span data-ttu-id="89ce5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="89ce5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="89ce5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<chování**](behavior-of-endpointbehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="89ce5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="89ce5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="89ce5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="89ce5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<třídy issuedtoken >**</span><span class="sxs-lookup"><span data-stu-id="89ce5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89ce5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89ce5-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89ce5-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="89ce5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="89ce5-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="89ce5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89ce5-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="89ce5-113">Attributes</span></span>  
  
|<span data-ttu-id="89ce5-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="89ce5-114">Attribute</span></span>|<span data-ttu-id="89ce5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="89ce5-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="89ce5-116">Volitelný logický atribut, který určuje, zda jsou tokeny uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="89ce5-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="89ce5-117">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="89ce5-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="89ce5-118">Volitelný řetězcový atribut určující, které náhodné hodnoty (jenž) se používají pro operace handshake.</span><span class="sxs-lookup"><span data-stu-id="89ce5-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="89ce5-119">Mezi hodnoty patří `ClientEntropy`, `ServerEntropy`a `CombinedEntropy`, výchozí hodnota je `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="89ce5-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="89ce5-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="89ce5-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="89ce5-121">Volitelný celočíselný atribut, který určuje procentuální hodnotu platného časového rámce (poskytnutý vystavitelem tokenu), který může uplynout před obnovením tokenu.</span><span class="sxs-lookup"><span data-stu-id="89ce5-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="89ce5-122">Hodnoty jsou od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="89ce5-122">Values are from 0 to 100.</span></span> <span data-ttu-id="89ce5-123">Výchozí hodnota je 60, která určuje 60% času průchodu před pokusem o obnovení.</span><span class="sxs-lookup"><span data-stu-id="89ce5-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="89ce5-124">Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="89ce5-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="89ce5-125">Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s místním vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="89ce5-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="89ce5-126">Volitelný atribut TimeSpan, který určuje dobu, po kterou jsou vydané tokeny ukládány do mezipaměti v případě, že Vystavitel tokenů (STS) neurčuje čas.</span><span class="sxs-lookup"><span data-stu-id="89ce5-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="89ce5-127">Výchozí hodnota je "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="89ce5-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89ce5-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="89ce5-128">Child Elements</span></span>  
  
|<span data-ttu-id="89ce5-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="89ce5-129">Element</span></span>|<span data-ttu-id="89ce5-130">Popis</span><span class="sxs-lookup"><span data-stu-id="89ce5-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89ce5-131">\<localIssuer ></span><span class="sxs-lookup"><span data-stu-id="89ce5-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="89ce5-132">Určuje adresu místního vystavitele tokenu a vazbu, která se používá ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="89ce5-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="89ce5-133">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="89ce5-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="89ce5-134">Určuje chování koncového bodu, které se má použít při kontaktování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="89ce5-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89ce5-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="89ce5-135">Parent Elements</span></span>  
  
|<span data-ttu-id="89ce5-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="89ce5-136">Element</span></span>|<span data-ttu-id="89ce5-137">Popis</span><span class="sxs-lookup"><span data-stu-id="89ce5-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="89ce5-138">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="89ce5-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="89ce5-139">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="89ce5-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89ce5-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89ce5-140">Remarks</span></span>  
 <span data-ttu-id="89ce5-141">Vydaný token je vlastní typ přihlašovacích údajů, který se používá například při ověřování pomocí služby tokenů zabezpečení (STS) ve federovaném scénáři.</span><span class="sxs-lookup"><span data-stu-id="89ce5-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="89ce5-142">Ve výchozím nastavení je tokenem token SAML.</span><span class="sxs-lookup"><span data-stu-id="89ce5-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="89ce5-143">Další informace najdete v tématech [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)a [federační a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="89ce5-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="89ce5-144">Tato část obsahuje prvky, které slouží ke konfiguraci místního vystavitele tokenů nebo chování používaného se službou tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="89ce5-144">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="89ce5-145">Pokyny ke konfiguraci klienta pro použití místního vystavitele najdete v tématu [Postupy: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="89ce5-145">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89ce5-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89ce5-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="89ce5-147">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="89ce5-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="89ce5-148">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="89ce5-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="89ce5-149">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="89ce5-149">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="89ce5-150">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="89ce5-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="89ce5-151">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="89ce5-151">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="89ce5-152">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="89ce5-152">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="89ce5-153">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="89ce5-153">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
