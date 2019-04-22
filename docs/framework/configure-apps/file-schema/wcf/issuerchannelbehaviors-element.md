---
title: Element <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 7cbd50daa82b0ca937a1bba93786545898b03c8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58890472"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="d8d4e-102">\<issuerChannelBehaviors> Element</span><span class="sxs-lookup"><span data-stu-id="d8d4e-102">\<issuerChannelBehaviors> Element</span></span>

<span data-ttu-id="d8d4e-103">Obsahuje kolekci chování koncového bodu klienta Windows Communication Foundation (WCF) (definované v konfiguraci) se použije při komunikaci s určeným službám tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="d8d4e-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="d8d4e-104">Chování definované nemůže obsahovat [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="d8d4e-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a><span data-ttu-id="d8d4e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8d4e-105">Syntax</span></span>

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8d4e-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d8d4e-106">Attributes and Elements</span></span>

<span data-ttu-id="d8d4e-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d8d4e-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8d4e-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="d8d4e-108">Attributes</span></span>

<span data-ttu-id="d8d4e-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="d8d4e-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8d4e-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d8d4e-110">Child Elements</span></span>

|<span data-ttu-id="d8d4e-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8d4e-111">Element</span></span>|<span data-ttu-id="d8d4e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d8d4e-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8d4e-113">\<add></span><span class="sxs-lookup"><span data-stu-id="d8d4e-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="d8d4e-114">Přidá do kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="d8d4e-114">Adds a behavior to the collection.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d8d4e-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d8d4e-115">Parent Elements</span></span>

|<span data-ttu-id="d8d4e-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="d8d4e-116">Element</span></span>|<span data-ttu-id="d8d4e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d8d4e-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8d4e-118">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="d8d4e-118">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="d8d4e-119">Určuje vlastní token pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="d8d4e-119">Specifies a custom token used to authenticate a client to a service.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8d4e-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8d4e-120">Remarks</span></span>

<span data-ttu-id="d8d4e-121">Tento prvek, pokud žádný chování (jiné než chování, které zahrnují `<clientCredentials>` elementy) musí být použita ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="d8d4e-121">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="d8d4e-122">Například pokud [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) chování element musí být zahrnut.</span><span class="sxs-lookup"><span data-stu-id="d8d4e-122">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8d4e-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8d4e-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="d8d4e-124">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="d8d4e-124">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d8d4e-125">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d8d4e-125">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="d8d4e-126">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d8d4e-126">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d8d4e-127">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d8d4e-127">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d8d4e-128">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="d8d4e-128">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="d8d4e-129">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="d8d4e-129">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="d8d4e-130">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="d8d4e-130">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="d8d4e-131">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d8d4e-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
