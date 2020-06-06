---
title: Element <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
no-loc:
- <system.serviceModel>
- <behaviors>
- <endpointBehaviors>
- <behavior>
- <clientCredentials>
- <issuedToken>
- <issuerChannelBehaviors>
- <dataContractSerializer>
ms.openlocfilehash: cbbfb9d3b5af47a360aa82cf837cd6749f61b641
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70893154"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="6e8ae-102">Element \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="6e8ae-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="6e8ae-103">Obsahuje kolekci chování koncového bodu klienta služby Windows Communication Foundation (WCF) (definované v konfiguraci), která se má použít při komunikaci se zadanými službami tokenů služeb.</span><span class="sxs-lookup"><span data-stu-id="6e8ae-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="6e8ae-104">Definované chování nemůže obsahovat žádné [\<clientCredentials>](clientcredentials.md) prvky.</span><span class="sxs-lookup"><span data-stu-id="6e8ae-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors>

## <a name="syntax"></a><span data-ttu-id="6e8ae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e8ae-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6e8ae-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6e8ae-106">Attributes and elements</span></span>

<span data-ttu-id="6e8ae-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6e8ae-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6e8ae-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="6e8ae-108">Attributes</span></span>

<span data-ttu-id="6e8ae-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="6e8ae-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6e8ae-110">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6e8ae-110">Child elements</span></span>

|<span data-ttu-id="6e8ae-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e8ae-111">Element</span></span>|<span data-ttu-id="6e8ae-112">Description</span><span class="sxs-lookup"><span data-stu-id="6e8ae-112">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="6e8ae-113">Přidá chování do kolekce.</span><span class="sxs-lookup"><span data-stu-id="6e8ae-113">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6e8ae-114">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6e8ae-114">Parent elements</span></span>

|<span data-ttu-id="6e8ae-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="6e8ae-115">Element</span></span>|<span data-ttu-id="6e8ae-116">Description</span><span class="sxs-lookup"><span data-stu-id="6e8ae-116">Description</span></span>|
|-------------|-----------------|
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="6e8ae-117">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="6e8ae-117">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6e8ae-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e8ae-118">Remarks</span></span>

<span data-ttu-id="6e8ae-119">Tento prvek použijte v případě, že `<clientCredentials>` ke komunikaci se službou je nutné použít jakékoli chování (jiné než chování, které zahrnuje prvky).</span><span class="sxs-lookup"><span data-stu-id="6e8ae-119">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="6e8ae-120">Například, pokud [\<dataContractSerializer>](datacontractserializer-element.md) musí být zahrnut prvek chování.</span><span class="sxs-lookup"><span data-stu-id="6e8ae-120">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e8ae-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e8ae-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="6e8ae-122">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="6e8ae-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6e8ae-123">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6e8ae-123">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6e8ae-124">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="6e8ae-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6e8ae-125">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6e8ae-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6e8ae-126">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="6e8ae-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="6e8ae-127">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="6e8ae-127">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="6e8ae-128">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="6e8ae-128">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="6e8ae-129">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="6e8ae-129">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
