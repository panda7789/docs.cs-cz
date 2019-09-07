---
title: Element <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 2c0e0d8d041565edd25c4b2c2802bfd2a589b4f7
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397904"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="0fff5-102">\<issuerChannelBehaviors – element ></span><span class="sxs-lookup"><span data-stu-id="0fff5-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="0fff5-103">Obsahuje kolekci chování koncového bodu klienta služby Windows Communication Foundation (WCF) (definované v konfiguraci), která se má použít při komunikaci se zadanými službami tokenů služeb.</span><span class="sxs-lookup"><span data-stu-id="0fff5-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="0fff5-104">Definované chování nesmí obsahovat žádné [ \<prvky > ClientCredentials](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="0fff5-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

<span data-ttu-id="0fff5-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0fff5-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0fff5-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0fff5-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0fff5-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0fff5-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="0fff5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0fff5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="0fff5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="0fff5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="0fff5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="0fff5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="0fff5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Třídy IssuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="0fff5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="0fff5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerChannelBehaviors >**</span><span class="sxs-lookup"><span data-stu-id="0fff5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerChannelBehaviors>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="0fff5-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fff5-113">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0fff5-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0fff5-114">Attributes and Elements</span></span>

<span data-ttu-id="0fff5-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0fff5-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0fff5-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="0fff5-116">Attributes</span></span>

<span data-ttu-id="0fff5-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="0fff5-117">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0fff5-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0fff5-118">Child Elements</span></span>

|<span data-ttu-id="0fff5-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="0fff5-119">Element</span></span>|<span data-ttu-id="0fff5-120">Popis</span><span class="sxs-lookup"><span data-stu-id="0fff5-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0fff5-121">\<add></span><span class="sxs-lookup"><span data-stu-id="0fff5-121">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="0fff5-122">Přidá chování do kolekce.</span><span class="sxs-lookup"><span data-stu-id="0fff5-122">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0fff5-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0fff5-123">Parent Elements</span></span>

|<span data-ttu-id="0fff5-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0fff5-124">Element</span></span>|<span data-ttu-id="0fff5-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0fff5-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0fff5-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="0fff5-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="0fff5-127">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="0fff5-127">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0fff5-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fff5-128">Remarks</span></span>

<span data-ttu-id="0fff5-129">Tento prvek použijte v případě, že ke komunikaci se službou je `<clientCredentials>` nutné použít jakékoli chování (jiné než chování, které zahrnuje prvky).</span><span class="sxs-lookup"><span data-stu-id="0fff5-129">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="0fff5-130">Například, pokud [ \<](datacontractserializer-element.md) je třeba zahrnout prvek chování > DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="0fff5-130">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fff5-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fff5-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="0fff5-132">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="0fff5-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="0fff5-133">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0fff5-133">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0fff5-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="0fff5-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="0fff5-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0fff5-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0fff5-136">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="0fff5-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="0fff5-137">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="0fff5-137">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="0fff5-138">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="0fff5-138">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="0fff5-139">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="0fff5-139">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
