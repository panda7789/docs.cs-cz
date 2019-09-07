---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: b5ab3c3ad070499d686ea74b9fd459e89f380cfa
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397966"
---
# <a name="issuedtoken"></a><span data-ttu-id="60fac-101">\<Třídy IssuedToken ></span><span class="sxs-lookup"><span data-stu-id="60fac-101">\<issuedToken></span></span>
<span data-ttu-id="60fac-102">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="60fac-102">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
<span data-ttu-id="60fac-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="60fac-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="60fac-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="60fac-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="60fac-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="60fac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="60fac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="60fac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="60fac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="60fac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="60fac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="60fac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="60fac-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Třídy IssuedToken >**</span><span class="sxs-lookup"><span data-stu-id="60fac-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60fac-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60fac-110">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60fac-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="60fac-111">Attributes and Elements</span></span>  
 <span data-ttu-id="60fac-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="60fac-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60fac-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="60fac-113">Attributes</span></span>  
  
|<span data-ttu-id="60fac-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="60fac-114">Attribute</span></span>|<span data-ttu-id="60fac-115">Popis</span><span class="sxs-lookup"><span data-stu-id="60fac-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="60fac-116">Volitelný logický atribut, který určuje, zda jsou tokeny uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="60fac-116">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="60fac-117">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="60fac-117">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="60fac-118">Volitelný řetězcový atribut určující, které náhodné hodnoty (jenž) se používají pro operace handshake.</span><span class="sxs-lookup"><span data-stu-id="60fac-118">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="60fac-119">Mezi hodnoty `ClientEntropy`patří `ServerEntropy`, a `CombinedEntropy`. výchozí hodnota je `CombinedEntropy`.</span><span class="sxs-lookup"><span data-stu-id="60fac-119">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="60fac-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span><span class="sxs-lookup"><span data-stu-id="60fac-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="60fac-121">Volitelný celočíselný atribut, který určuje procentuální hodnotu platného časového rámce (poskytnutý vystavitelem tokenu), který může uplynout před obnovením tokenu.</span><span class="sxs-lookup"><span data-stu-id="60fac-121">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="60fac-122">Hodnoty jsou od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="60fac-122">Values are from 0 to 100.</span></span> <span data-ttu-id="60fac-123">Výchozí hodnota je 60, která určuje 60% času průchodu před pokusem o obnovení.</span><span class="sxs-lookup"><span data-stu-id="60fac-123">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="60fac-124">Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="60fac-124">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="60fac-125">Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s místním vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="60fac-125">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="60fac-126">Volitelný atribut TimeSpan, který určuje dobu, po kterou jsou vydané tokeny ukládány do mezipaměti v případě, že Vystavitel tokenů (STS) neurčuje čas.</span><span class="sxs-lookup"><span data-stu-id="60fac-126">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="60fac-127">Výchozí hodnota je "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="60fac-127">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60fac-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="60fac-128">Child Elements</span></span>  
  
|<span data-ttu-id="60fac-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="60fac-129">Element</span></span>|<span data-ttu-id="60fac-130">Popis</span><span class="sxs-lookup"><span data-stu-id="60fac-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60fac-131">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="60fac-131">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="60fac-132">Určuje adresu místního vystavitele tokenu a vazbu, která se používá ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="60fac-132">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[<span data-ttu-id="60fac-133">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="60fac-133">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="60fac-134">Určuje chování koncového bodu, které se má použít při kontaktování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="60fac-134">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60fac-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="60fac-135">Parent Elements</span></span>  
  
|<span data-ttu-id="60fac-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="60fac-136">Element</span></span>|<span data-ttu-id="60fac-137">Popis</span><span class="sxs-lookup"><span data-stu-id="60fac-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60fac-138">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="60fac-138">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="60fac-139">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="60fac-139">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60fac-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60fac-140">Remarks</span></span>  
 <span data-ttu-id="60fac-141">Vydaný token je vlastní typ přihlašovacích údajů, který se používá například při ověřování pomocí služby tokenů zabezpečení (STS) ve federovaném scénáři.</span><span class="sxs-lookup"><span data-stu-id="60fac-141">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="60fac-142">Ve výchozím nastavení je tokenem token SAML.</span><span class="sxs-lookup"><span data-stu-id="60fac-142">By default, the token is a SAML token.</span></span> <span data-ttu-id="60fac-143">Další informace najdete v tématu [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="60fac-143">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span> <span data-ttu-id="60fac-144">a [federačních a vydaných tokenů](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="60fac-144">and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="60fac-145">Tato část obsahuje prvky, které slouží ke konfiguraci místního vystavitele tokenů nebo chování používaného se službou tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="60fac-145">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="60fac-146">Pokyny ke konfiguraci klienta pro použití místního vystavitele najdete v tématu [How to: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="60fac-146">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60fac-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60fac-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="60fac-148">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="60fac-148">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="60fac-149">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="60fac-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="60fac-150">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="60fac-150">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="60fac-151">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="60fac-151">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="60fac-152">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="60fac-152">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="60fac-153">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="60fac-153">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="60fac-154">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="60fac-154">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
