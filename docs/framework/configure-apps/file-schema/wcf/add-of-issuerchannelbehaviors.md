---
title: <add> z <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 5c9937cb6302a194228461f3e2e06ecdf4d43269
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673612"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="8cca7-102">\<add> of \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="8cca7-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="8cca7-103">Přidá chování koncového bodu se použije při komunikaci se službou tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8cca7-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="8cca7-104">Pokud jakékoliv chování koncového bodu obsahuje [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8cca7-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>

<span data-ttu-id="8cca7-105">\<system.ServiceModel>\\</span><span class="sxs-lookup"><span data-stu-id="8cca7-105">\<system.ServiceModel>\\</span></span>
<span data-ttu-id="8cca7-106">\<chování > \\</span><span class="sxs-lookup"><span data-stu-id="8cca7-106">\<behaviors>\\</span></span>
<span data-ttu-id="8cca7-107">názvy endpointBehaviors části \<chování > \\</span><span class="sxs-lookup"><span data-stu-id="8cca7-107">endpointBehaviors section \<behavior>\\</span></span>
<span data-ttu-id="8cca7-108">\<clientCredentials>\\</span><span class="sxs-lookup"><span data-stu-id="8cca7-108">\<clientCredentials>\\</span></span>
<span data-ttu-id="8cca7-109">\<issuedToken>\\</span><span class="sxs-lookup"><span data-stu-id="8cca7-109">\<issuedToken>\\</span></span>
<span data-ttu-id="8cca7-110">\<issuerChannelBehaviors > Element\\</span><span class="sxs-lookup"><span data-stu-id="8cca7-110">\<issuerChannelBehaviors> Element\\</span></span>
<span data-ttu-id="8cca7-111">\<add></span><span class="sxs-lookup"><span data-stu-id="8cca7-111">\<add></span></span>

## <a name="syntax"></a><span data-ttu-id="8cca7-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cca7-112">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8cca7-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8cca7-113">Attributes and Elements</span></span>

<span data-ttu-id="8cca7-114">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8cca7-114">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="8cca7-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="8cca7-115">Attributes</span></span>

|<span data-ttu-id="8cca7-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="8cca7-116">Attribute</span></span>|<span data-ttu-id="8cca7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="8cca7-117">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="8cca7-118">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="8cca7-118">issuerAddress</span></span>|<span data-ttu-id="8cca7-119">Identifikátor URI vystavitele tokenu zabezpečení komunikovat.</span><span class="sxs-lookup"><span data-stu-id="8cca7-119">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="8cca7-120">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="8cca7-120">behaviorConfiguration</span></span>|<span data-ttu-id="8cca7-121">Název chování koncového bodu definované ve stejném souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8cca7-121">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8cca7-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8cca7-122">Child Elements</span></span>

<span data-ttu-id="8cca7-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="8cca7-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8cca7-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8cca7-124">Parent Elements</span></span>

|<span data-ttu-id="8cca7-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="8cca7-125">Element</span></span>|<span data-ttu-id="8cca7-126">Popis</span><span class="sxs-lookup"><span data-stu-id="8cca7-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8cca7-127">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="8cca7-127">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="8cca7-128">Obsahuje kolekci chování koncového bodu klienta Windows Communication Foundation (WCF) se použije při komunikaci s určeným službám tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="8cca7-128">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8cca7-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8cca7-129">Remarks</span></span>

<span data-ttu-id="8cca7-130">`issuerAddress` obsahuje identifikátor URI, který chce komunikaci s klientem služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8cca7-130">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="8cca7-131">`behaviorConfiguration` odkazuje na chování koncového bodu, který aplikace používá v kanálech vytvořené technologií Windows Communication Foundation (WCF) Chcete-li získat od služby tokenů zabezpečení vydané tokeny.</span><span class="sxs-lookup"><span data-stu-id="8cca7-131">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cca7-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cca7-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="8cca7-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="8cca7-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8cca7-134">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8cca7-134">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="8cca7-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="8cca7-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8cca7-136">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8cca7-136">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8cca7-137">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="8cca7-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="8cca7-138">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="8cca7-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="8cca7-139">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="8cca7-139">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="8cca7-140">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="8cca7-140">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="8cca7-141">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="8cca7-141">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
