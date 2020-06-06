---
title: <add> z <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398332"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="72f16-102">\<add> z \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="72f16-102">\<add> of \<issuerChannelBehaviors></span></span>

<span data-ttu-id="72f16-103">Přidá chování koncového bodu, které se použije při komunikaci se službou STS.</span><span class="sxs-lookup"><span data-stu-id="72f16-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>

> [!NOTE]
> <span data-ttu-id="72f16-104">Pokud jakékoli chování koncového bodu obsahuje [\<clientCredentials>](clientcredentials.md) element, vyvolá se výjimka.</span><span class="sxs-lookup"><span data-stu-id="72f16-104">If any endpoint behavior contains a [\<clientCredentials>](clientcredentials.md) element, an exception will be thrown.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedToken>**](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerChannelBehaviors>**](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

## <a name="syntax"></a><span data-ttu-id="72f16-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72f16-105">Syntax</span></span>

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="72f16-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="72f16-106">Attributes and Elements</span></span>

<span data-ttu-id="72f16-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="72f16-107">The following sections describe attributes, child elements, and parent elements</span></span>

### <a name="attributes"></a><span data-ttu-id="72f16-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="72f16-108">Attributes</span></span>

|<span data-ttu-id="72f16-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="72f16-109">Attribute</span></span>|<span data-ttu-id="72f16-110">Popis</span><span class="sxs-lookup"><span data-stu-id="72f16-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="72f16-111">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="72f16-111">issuerAddress</span></span>|<span data-ttu-id="72f16-112">Identifikátor URI vystavitele tokenu zabezpečení, se kterým se má komunikovat.</span><span class="sxs-lookup"><span data-stu-id="72f16-112">The URI of the security token issuer to communicate with.</span></span>|
|<span data-ttu-id="72f16-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="72f16-113">behaviorConfiguration</span></span>|<span data-ttu-id="72f16-114">Název chování koncového bodu, které je definováno ve stejném konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="72f16-114">The name of an endpoint behavior defined in the same configuration file.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="72f16-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="72f16-115">Child Elements</span></span>

<span data-ttu-id="72f16-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="72f16-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="72f16-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="72f16-117">Parent Elements</span></span>

|<span data-ttu-id="72f16-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="72f16-118">Element</span></span>|<span data-ttu-id="72f16-119">Description</span><span class="sxs-lookup"><span data-stu-id="72f16-119">Description</span></span>|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|<span data-ttu-id="72f16-120">Obsahuje kolekci chování koncového bodu klienta služby Windows Communication Foundation (WCF), která se má použít při komunikaci se zadanými službami tokenů služeb.</span><span class="sxs-lookup"><span data-stu-id="72f16-120">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|

## <a name="remarks"></a><span data-ttu-id="72f16-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72f16-121">Remarks</span></span>

<span data-ttu-id="72f16-122">`issuerAddress`obsahuje identifikátor URI služby tokenu zabezpečení, se kterou chce klient komunikovat.</span><span class="sxs-lookup"><span data-stu-id="72f16-122">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="72f16-123">`behaviorConfiguration`odkazuje na chování koncového bodu, které aplikace používá v kanálech vytvořených pomocí Windows Communication Foundation (WCF) k získání vydaných tokenů ze služeb tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="72f16-123">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="72f16-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="72f16-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="72f16-125">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="72f16-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="72f16-126">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="72f16-126">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="72f16-127">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="72f16-127">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="72f16-128">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="72f16-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="72f16-129">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="72f16-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="72f16-130">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="72f16-130">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="72f16-131">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="72f16-131">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="72f16-132">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="72f16-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
