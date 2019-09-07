---
title: <add> z <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398332"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="e61dc-102">\<Přidat > \<> issuerChannelBehaviors</span><span class="sxs-lookup"><span data-stu-id="e61dc-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="e61dc-103">Přidá chování koncového bodu, které se použije při komunikaci se službou STS.</span><span class="sxs-lookup"><span data-stu-id="e61dc-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="e61dc-104">Pokud jakékoli chování koncového bodu obsahuje [ \<prvek ClientCredentials >](clientcredentials.md) , vyvolá se výjimka.</span><span class="sxs-lookup"><span data-stu-id="e61dc-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="e61dc-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e61dc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e61dc-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e61dc-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e61dc-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e61dc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="e61dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e61dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="e61dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e61dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="e61dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e61dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="e61dc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Třídy IssuedToken >** ](issuedtoken.md)</span><span class="sxs-lookup"><span data-stu-id="e61dc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)</span></span>\
<span data-ttu-id="e61dc-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerChannelBehaviors >** ](issuerchannelbehaviors-element.md)</span><span class="sxs-lookup"><span data-stu-id="e61dc-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)</span></span>\
<span data-ttu-id="e61dc-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="e61dc-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="e61dc-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e61dc-114">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e61dc-115">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e61dc-115">Attributes and Elements</span></span>

<span data-ttu-id="e61dc-116">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e61dc-116">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="e61dc-117">Atributy</span><span class="sxs-lookup"><span data-stu-id="e61dc-117">Attributes</span></span>

|<span data-ttu-id="e61dc-118">Atribut</span><span class="sxs-lookup"><span data-stu-id="e61dc-118">Attribute</span></span>|<span data-ttu-id="e61dc-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e61dc-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="e61dc-120">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="e61dc-120">issuerAddress</span></span>|<span data-ttu-id="e61dc-121">Identifikátor URI vystavitele tokenu zabezpečení, se kterým se má komunikovat.</span><span class="sxs-lookup"><span data-stu-id="e61dc-121">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="e61dc-122">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e61dc-122">behaviorConfiguration</span></span>|<span data-ttu-id="e61dc-123">Název chování koncového bodu, které je definováno ve stejném konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="e61dc-123">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e61dc-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e61dc-124">Child Elements</span></span>

<span data-ttu-id="e61dc-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="e61dc-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e61dc-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e61dc-126">Parent Elements</span></span>

|<span data-ttu-id="e61dc-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="e61dc-127">Element</span></span>|<span data-ttu-id="e61dc-128">Popis</span><span class="sxs-lookup"><span data-stu-id="e61dc-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e61dc-129">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="e61dc-129">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="e61dc-130">Obsahuje kolekci chování koncového bodu klienta služby Windows Communication Foundation (WCF), která se má použít při komunikaci se zadanými službami tokenů služeb.</span><span class="sxs-lookup"><span data-stu-id="e61dc-130">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e61dc-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e61dc-131">Remarks</span></span>

<span data-ttu-id="e61dc-132">`issuerAddress`obsahuje identifikátor URI služby tokenu zabezpečení, se kterou chce klient komunikovat.</span><span class="sxs-lookup"><span data-stu-id="e61dc-132">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="e61dc-133">`behaviorConfiguration`odkazuje na chování koncového bodu, které aplikace používá v kanálech vytvořených pomocí Windows Communication Foundation (WCF) k získání vydaných tokenů ze služeb tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e61dc-133">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="e61dc-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e61dc-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="e61dc-135">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="e61dc-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e61dc-136">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e61dc-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e61dc-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="e61dc-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e61dc-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e61dc-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e61dc-139">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="e61dc-139">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="e61dc-140">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="e61dc-140">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="e61dc-141">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="e61dc-141">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="e61dc-142">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="e61dc-142">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e61dc-143">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="e61dc-143">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
