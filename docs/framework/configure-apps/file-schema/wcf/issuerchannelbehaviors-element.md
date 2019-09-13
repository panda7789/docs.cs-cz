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
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893154"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="87d15-102">\<issuerChannelBehaviors – element ></span><span class="sxs-lookup"><span data-stu-id="87d15-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="87d15-103">Obsahuje kolekci chování koncového bodu klienta služby Windows Communication Foundation (WCF) (definované v konfiguraci), která se má použít při komunikaci se zadanými službami tokenů služeb.</span><span class="sxs-lookup"><span data-stu-id="87d15-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="87d15-104">Definované chování nesmí obsahovat žádné [ \<prvky > ClientCredentials](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="87d15-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="87d15-105">[\<> Konfigurace](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87d15-105">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="87d15-106">&nbsp;&nbsp;[\<System. serviceModel >](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="87d15-106">&nbsp;&nbsp;[\<system.serviceModel>](system-servicemodel.md)</span></span>\
<span data-ttu-id="87d15-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<> chování](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="87d15-107">&nbsp;&nbsp;&nbsp;&nbsp;[\<behaviors>](behaviors.md)</span></span>\
<span data-ttu-id="87d15-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors >](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="87d15-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<endpointBehaviors>](endpointbehaviors.md)</span></span>\
<span data-ttu-id="87d15-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> chování](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="87d15-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<behavior>](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="87d15-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<> clientCredentials](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="87d15-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clientCredentials>](clientcredentials.md)</span></span>\
<span data-ttu-id="87d15-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Třídy IssuedToken >](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="87d15-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<issuedToken>](issuedtoken.md)</span></span>\
<span data-ttu-id="87d15-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="87d15-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<issuerChannelBehaviors></span></span>

## <a name="syntax"></a><span data-ttu-id="87d15-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87d15-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87d15-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87d15-114">Attributes and elements</span></span>

<span data-ttu-id="87d15-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87d15-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="87d15-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="87d15-116">Attributes</span></span>

<span data-ttu-id="87d15-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="87d15-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87d15-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="87d15-118">Child elements</span></span>

|<span data-ttu-id="87d15-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="87d15-119">Element</span></span>|<span data-ttu-id="87d15-120">Popis</span><span class="sxs-lookup"><span data-stu-id="87d15-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87d15-121">\<add></span><span class="sxs-lookup"><span data-stu-id="87d15-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="87d15-122">Přidá chování do kolekce.</span><span class="sxs-lookup"><span data-stu-id="87d15-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="87d15-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="87d15-123">Parent elements</span></span>

|<span data-ttu-id="87d15-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="87d15-124">Element</span></span>|<span data-ttu-id="87d15-125">Popis</span><span class="sxs-lookup"><span data-stu-id="87d15-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87d15-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="87d15-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="87d15-127">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="87d15-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="87d15-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87d15-128">Remarks</span></span>

<span data-ttu-id="87d15-129">Tento prvek použijte v případě, že ke komunikaci se službou je `<clientCredentials>` nutné použít jakékoli chování (jiné než chování, které zahrnuje prvky).</span><span class="sxs-lookup"><span data-stu-id="87d15-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="87d15-130">Například, pokud [ \<](datacontractserializer-element.md) je třeba zahrnout prvek chování > DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="87d15-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="87d15-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87d15-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="87d15-132">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="87d15-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="87d15-133">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="87d15-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="87d15-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="87d15-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="87d15-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="87d15-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="87d15-136">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="87d15-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="87d15-137">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="87d15-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="87d15-138">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="87d15-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="87d15-139">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="87d15-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
