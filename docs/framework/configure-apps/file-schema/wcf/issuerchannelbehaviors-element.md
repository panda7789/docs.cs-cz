---
title: Element <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: e0e41b4f6d66cd4455c43dda7c77798553f2b58f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929927"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="a25a8-102">\<issuerChannelBehaviors – element ></span><span class="sxs-lookup"><span data-stu-id="a25a8-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="a25a8-103">Obsahuje kolekci chování koncového bodu klienta služby Windows Communication Foundation (WCF) (definované v konfiguraci), která se má použít při komunikaci se zadanými službami tokenů služeb.</span><span class="sxs-lookup"><span data-stu-id="a25a8-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="a25a8-104">Definované chování nesmí obsahovat žádné [ \<prvky > ClientCredentials](clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="a25a8-104">The defined behaviors cannot include any [\<clientCredentials>](clientcredentials.md) elements.</span></span>

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a><span data-ttu-id="a25a8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a25a8-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a25a8-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a25a8-106">Attributes and Elements</span></span>

<span data-ttu-id="a25a8-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a25a8-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a25a8-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="a25a8-108">Attributes</span></span>

<span data-ttu-id="a25a8-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="a25a8-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a25a8-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a25a8-110">Child Elements</span></span>

|<span data-ttu-id="a25a8-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="a25a8-111">Element</span></span>|<span data-ttu-id="a25a8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a25a8-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a25a8-113">\<add></span><span class="sxs-lookup"><span data-stu-id="a25a8-113">\<add></span></span>](add-of-issuerchannelbehaviors.md)|<span data-ttu-id="a25a8-114">Přidá chování do kolekce.</span><span class="sxs-lookup"><span data-stu-id="a25a8-114">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a25a8-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a25a8-115">Parent Elements</span></span>

|<span data-ttu-id="a25a8-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="a25a8-116">Element</span></span>|<span data-ttu-id="a25a8-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a25a8-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a25a8-118">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="a25a8-118">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="a25a8-119">Určuje vlastní token, který slouží k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="a25a8-119">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a25a8-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a25a8-120">Remarks</span></span>

<span data-ttu-id="a25a8-121">Tento prvek použijte v případě, že ke komunikaci se službou je `<clientCredentials>` nutné použít jakékoli chování (jiné než chování, které zahrnuje prvky).</span><span class="sxs-lookup"><span data-stu-id="a25a8-121">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="a25a8-122">Například, pokud [ \<](datacontractserializer-element.md) je třeba zahrnout prvek chování > DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="a25a8-122">For example, if a [\<dataContractSerializer>](datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="a25a8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a25a8-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="a25a8-124">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="a25a8-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a25a8-125">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a25a8-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a25a8-126">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a25a8-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a25a8-127">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a25a8-127">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a25a8-128">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="a25a8-128">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a25a8-129">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="a25a8-129">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a25a8-130">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="a25a8-130">How to: Configure a Local Issuer</span></span>](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="a25a8-131">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a25a8-131">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
