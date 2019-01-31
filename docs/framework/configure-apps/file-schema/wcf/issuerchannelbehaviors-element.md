---
title: Element <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 624848db4cead14e46c97bba7404adcb65e43d4d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274137"
---
# <a name="issuerchannelbehaviors-element"></a><span data-ttu-id="f5a1e-102">\<issuerChannelBehaviors> Element</span><span class="sxs-lookup"><span data-stu-id="f5a1e-102">\<issuerChannelBehaviors> Element</span></span>
<span data-ttu-id="f5a1e-103">Obsahuje kolekci chování koncového bodu klienta Windows Communication Foundation (WCF) (definované v konfiguraci) se použije při komunikaci s určeným službám tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="f5a1e-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="f5a1e-104">Chování definované nemůže obsahovat [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="f5a1e-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="f5a1e-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f5a1e-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f5a1e-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f5a1e-106">\<behaviors></span></span>  
<span data-ttu-id="f5a1e-107">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="f5a1e-107">endpointBehaviors section</span></span>  
<span data-ttu-id="f5a1e-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f5a1e-108">\<behavior></span></span>  
<span data-ttu-id="f5a1e-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="f5a1e-109">\<clientCredentials></span></span>  
<span data-ttu-id="f5a1e-110">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="f5a1e-110">\<issuedToken></span></span>  
<span data-ttu-id="f5a1e-111">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="f5a1e-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5a1e-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5a1e-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>
  <add behaviorConfiguraton="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5a1e-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f5a1e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f5a1e-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f5a1e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5a1e-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="f5a1e-115">Attributes</span></span>  
 <span data-ttu-id="f5a1e-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="f5a1e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f5a1e-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f5a1e-117">Child Elements</span></span>  
  
|<span data-ttu-id="f5a1e-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="f5a1e-118">Element</span></span>|<span data-ttu-id="f5a1e-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f5a1e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5a1e-120">\<add></span><span class="sxs-lookup"><span data-stu-id="f5a1e-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="f5a1e-121">Přidá do kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="f5a1e-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f5a1e-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f5a1e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f5a1e-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="f5a1e-123">Element</span></span>|<span data-ttu-id="f5a1e-124">Popis</span><span class="sxs-lookup"><span data-stu-id="f5a1e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5a1e-125">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="f5a1e-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="f5a1e-126">Určuje vlastní token pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="f5a1e-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5a1e-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5a1e-127">Remarks</span></span>  
 <span data-ttu-id="f5a1e-128">Tento prvek, pokud žádný chování (jiné než chování, které zahrnují `<clientCredentials>` elementy) musí být použita ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="f5a1e-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="f5a1e-129">Například pokud [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) chování element musí být zahrnut.</span><span class="sxs-lookup"><span data-stu-id="f5a1e-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a1e-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5a1e-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="f5a1e-131">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="f5a1e-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f5a1e-132">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f5a1e-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f5a1e-133">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="f5a1e-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="f5a1e-134">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f5a1e-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f5a1e-135">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="f5a1e-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="f5a1e-136">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="f5a1e-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="f5a1e-137">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="f5a1e-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="f5a1e-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="f5a1e-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
