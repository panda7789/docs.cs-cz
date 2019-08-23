---
title: <add> z <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920112"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="a5545-102">\<Přidat > \<> issuerChannelBehaviors</span><span class="sxs-lookup"><span data-stu-id="a5545-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="a5545-103">Přidá chování koncového bodu, které se použije při komunikaci se službou STS.</span><span class="sxs-lookup"><span data-stu-id="a5545-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="a5545-104">Pokud jakékoli chování koncového bodu obsahuje [ \<prvek ClientCredentials >](clientcredentials.md) , vyvolá se výjimka.</span><span class="sxs-lookup"><span data-stu-id="a5545-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="a5545-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a5545-105">\<system.ServiceModel></span></span>\
<span data-ttu-id="a5545-106">\<> chování </span><span class="sxs-lookup"><span data-stu-id="a5545-106">\<behaviors></span></span>\
<span data-ttu-id="a5545-107">chování oddílu \<endpointBehaviors > </span><span class="sxs-lookup"><span data-stu-id="a5545-107">endpointBehaviors section \<behavior></span></span>\
<span data-ttu-id="a5545-108">\<clientCredentials > </span><span class="sxs-lookup"><span data-stu-id="a5545-108">\<clientCredentials></span></span>\
<span data-ttu-id="a5545-109">\<Třídy IssuedToken > </span><span class="sxs-lookup"><span data-stu-id="a5545-109">\<issuedToken></span></span>\
<span data-ttu-id="a5545-110">\<issuerChannelBehaviors > element </span><span class="sxs-lookup"><span data-stu-id="a5545-110">\<issuerChannelBehaviors> Element</span></span>\
<span data-ttu-id="a5545-111">\<add></span><span class="sxs-lookup"><span data-stu-id="a5545-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="a5545-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5545-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5545-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a5545-113">Attributes and Elements</span></span>

<span data-ttu-id="a5545-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a5545-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="a5545-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="a5545-115">Attributes</span></span>

|<span data-ttu-id="a5545-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="a5545-116">Attribute</span></span>|<span data-ttu-id="a5545-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a5545-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a5545-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="a5545-118">issuerAddress</span></span>|<span data-ttu-id="a5545-119">Identifikátor URI vystavitele tokenu zabezpečení, se kterým se má komunikovat.</span><span class="sxs-lookup"><span data-stu-id="a5545-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="a5545-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a5545-120">behaviorConfiguration</span></span>|<span data-ttu-id="a5545-121">Název chování koncového bodu, které je definováno ve stejném konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a5545-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a5545-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a5545-122">Child Elements</span></span>

<span data-ttu-id="a5545-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="a5545-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a5545-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a5545-124">Parent Elements</span></span>

|<span data-ttu-id="a5545-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="a5545-125">Element</span></span>|<span data-ttu-id="a5545-126">Popis</span><span class="sxs-lookup"><span data-stu-id="a5545-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5545-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="a5545-127">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)|<span data-ttu-id="a5545-128">Obsahuje kolekci chování koncového bodu klienta služby Windows Communication Foundation (WCF), která se má použít při komunikaci se zadanými službami tokenů služeb.</span><span class="sxs-lookup"><span data-stu-id="a5545-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a5545-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5545-129">Remarks</span></span>

<span data-ttu-id="a5545-130">`issuerAddress`obsahuje identifikátor URI služby tokenu zabezpečení, se kterou chce klient komunikovat.</span><span class="sxs-lookup"><span data-stu-id="a5545-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="a5545-131">`behaviorConfiguration`odkazuje na chování koncového bodu, které aplikace používá v kanálech vytvořených pomocí Windows Communication Foundation (WCF) k získání vydaných tokenů ze služeb tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a5545-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5545-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5545-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="a5545-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="a5545-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a5545-134">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a5545-134">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a5545-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a5545-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a5545-136">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a5545-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a5545-137">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="a5545-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a5545-138">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="a5545-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a5545-139">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="a5545-139">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="a5545-140">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a5545-140">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a5545-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="a5545-141">\<issuerChannelBehaviors></span></span>](issuerchannelbehaviors-element.md)
