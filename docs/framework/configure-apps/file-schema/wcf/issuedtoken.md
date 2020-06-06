---
title: <issuedToken>
ms.date: 03/30/2017
ms.assetid: b6eae4b7-a6cd-4e1a-b0f6-f407022550b0
ms.openlocfilehash: 56439748926ada642018f48a5787634a50d0f180
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "72846863"
---
# \<issuedToken>
<span data-ttu-id="cde76-101">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="cde76-101">Specifies a custom token used to authenticate a client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedToken>**  
  
## <a name="syntax"></a><span data-ttu-id="cde76-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cde76-102">Syntax</span></span>  
  
```xml  
<issuedToken cacheIssuedTokens="Boolean"
             defaultKeyEntropyMode="ClientEntropy/ServerEntropy/CombinedEntropy"
             issuedTokenRenewalThresholdPercentage = "0 to 100"
             issuerChannelBehaviors="String"
             localIssuerChannelBehaviors="String"
             maxIssuedTokenCachingTime="TimeSpan">
</issuedToken>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cde76-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cde76-103">Attributes and Elements</span></span>  
 <span data-ttu-id="cde76-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cde76-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cde76-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="cde76-105">Attributes</span></span>  
  
|<span data-ttu-id="cde76-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="cde76-106">Attribute</span></span>|<span data-ttu-id="cde76-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cde76-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheIssuedTokens`|<span data-ttu-id="cde76-108">Volitelný logický atribut, který určuje, zda jsou tokeny uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="cde76-108">Optional Boolean attribute that specifies whether tokens are cached.</span></span> <span data-ttu-id="cde76-109">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="cde76-109">The default is `true`.</span></span>|  
|`defaultKeyEntropyMode`|<span data-ttu-id="cde76-110">Volitelný řetězcový atribut určující, které náhodné hodnoty (jenž) se používají pro operace handshake.</span><span class="sxs-lookup"><span data-stu-id="cde76-110">Optional string attribute that specifies which random values (entropies) are used for handshake operations.</span></span> <span data-ttu-id="cde76-111">Mezi hodnoty patří `ClientEntropy` , `ServerEntropy` a `CombinedEntropy` . výchozí hodnota je `CombinedEntropy` .</span><span class="sxs-lookup"><span data-stu-id="cde76-111">Values include `ClientEntropy`, `ServerEntropy`, and `CombinedEntropy`, The default is `CombinedEntropy`.</span></span> <span data-ttu-id="cde76-112">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityKeyEntropyMode> .</span><span class="sxs-lookup"><span data-stu-id="cde76-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityKeyEntropyMode>.</span></span>|  
|`issuedTokenRenewalThresholdPercentage`|<span data-ttu-id="cde76-113">Volitelný celočíselný atribut, který určuje procentuální hodnotu platného časového rámce (poskytnutý vystavitelem tokenu), který může uplynout před obnovením tokenu.</span><span class="sxs-lookup"><span data-stu-id="cde76-113">Optional integer attribute that specifies the percentage of a valid time frame (supplied by the token issuer) that can pass before a token is renewed.</span></span> <span data-ttu-id="cde76-114">Hodnoty jsou od 0 do 100.</span><span class="sxs-lookup"><span data-stu-id="cde76-114">Values are from 0 to 100.</span></span> <span data-ttu-id="cde76-115">Výchozí hodnota je 60, která určuje 60% času průchodu před pokusem o obnovení.</span><span class="sxs-lookup"><span data-stu-id="cde76-115">The default is 60, which specifies 60% of the time passes before a renewal is attempted.</span></span>|  
|`issuerChannelBehaviors`|<span data-ttu-id="cde76-116">Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="cde76-116">Optional attribute that specifies the channel behaviors to use when communicating with the issuer.</span></span>|  
|`localIssuerChannelBehaviors`|<span data-ttu-id="cde76-117">Volitelný atribut, který určuje chování kanálu, které se má použít při komunikaci s místním vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="cde76-117">Optional attribute that specifies the channel behaviors to use when communicating with the local issuer.</span></span>|  
|`maxIssuedTokenCachingTime`|<span data-ttu-id="cde76-118">Volitelný atribut TimeSpan, který určuje dobu, po kterou jsou vydané tokeny ukládány do mezipaměti v případě, že Vystavitel tokenů (STS) neurčuje čas.</span><span class="sxs-lookup"><span data-stu-id="cde76-118">Optional Timespan attribute that specifies the duration that issued tokens are cached when the token issuer (an STS) does not specify a time.</span></span> <span data-ttu-id="cde76-119">Výchozí hodnota je "10675199.02:48:05.4775807."</span><span class="sxs-lookup"><span data-stu-id="cde76-119">The default is "10675199.02:48:05.4775807."</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cde76-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cde76-120">Child Elements</span></span>  
  
|<span data-ttu-id="cde76-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="cde76-121">Element</span></span>|<span data-ttu-id="cde76-122">Description</span><span class="sxs-lookup"><span data-stu-id="cde76-122">Description</span></span>|  
|-------------|-----------------|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="cde76-123">Určuje adresu místního vystavitele tokenu a vazbu, která se používá ke komunikaci s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="cde76-123">Specifies the address of the local issuer of the token and the binding used to communicate with the endpoint.</span></span>|  
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="cde76-124">Určuje chování koncového bodu, které se má použít při kontaktování místního vystavitele.</span><span class="sxs-lookup"><span data-stu-id="cde76-124">Specifies the endpoint behaviors to use when contacting a local issuer.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cde76-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cde76-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cde76-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="cde76-126">Element</span></span>|<span data-ttu-id="cde76-127">Description</span><span class="sxs-lookup"><span data-stu-id="cde76-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="cde76-128">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="cde76-128">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cde76-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cde76-129">Remarks</span></span>  
 <span data-ttu-id="cde76-130">Vydaný token je vlastní typ přihlašovacích údajů, který se používá například při ověřování pomocí služby tokenů zabezpečení (STS) ve federovaném scénáři.</span><span class="sxs-lookup"><span data-stu-id="cde76-130">An issued token is a custom credential type used, for example, when authenticating with a Secure Token Service (STS) in a federated scenario.</span></span> <span data-ttu-id="cde76-131">Ve výchozím nastavení je tokenem token SAML.</span><span class="sxs-lookup"><span data-stu-id="cde76-131">By default, the token is a SAML token.</span></span> <span data-ttu-id="cde76-132">Další informace najdete v tématech [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md)a [federační a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="cde76-132">For more information, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md), and [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="cde76-133">Tato část obsahuje prvky, které slouží ke konfiguraci místního vystavitele tokenů nebo chování používaného se službou tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cde76-133">This section contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="cde76-134">Pokyny ke konfiguraci klienta pro použití místního vystavitele najdete v tématu [Postupy: Konfigurace místního vystavitele](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="cde76-134">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](../../../wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde76-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="cde76-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.IssuedToken%2A>
- <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential>
- [<span data-ttu-id="cde76-136">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cde76-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="cde76-137">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="cde76-137">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cde76-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="cde76-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="cde76-139">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="cde76-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="cde76-140">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="cde76-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="cde76-141">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="cde76-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="cde76-142">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="cde76-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
