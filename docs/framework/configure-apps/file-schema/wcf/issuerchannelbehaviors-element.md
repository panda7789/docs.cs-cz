---
title: Element &lt;issuerChannelBehaviors&gt;
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: b77d0ce79557dff4b5a243da4d24703ed45fde07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677105"
---
# <a name="ltissuerchannelbehaviorsgt-element"></a><span data-ttu-id="71505-102">Element &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="71505-102">&lt;issuerChannelBehaviors&gt; Element</span></span>
<span data-ttu-id="71505-103">Obsahuje kolekci chování koncového bodu klienta Windows Communication Foundation (WCF) (definované v konfiguraci) se použije při komunikaci s určeným službám tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="71505-103">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors (defined in the configuration) to be used when communicating with the specified Service Token Services.</span></span> <span data-ttu-id="71505-104">Chování definované nemůže obsahovat [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementy.</span><span class="sxs-lookup"><span data-stu-id="71505-104">The defined behaviors cannot include any [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elements.</span></span>  
  
 <span data-ttu-id="71505-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="71505-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="71505-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="71505-106">\<behaviors></span></span>  
<span data-ttu-id="71505-107">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="71505-107">endpointBehaviors section</span></span>  
<span data-ttu-id="71505-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="71505-108">\<behavior></span></span>  
<span data-ttu-id="71505-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="71505-109">\<clientCredentials></span></span>  
<span data-ttu-id="71505-110">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="71505-110">\<issuedToken></span></span>  
<span data-ttu-id="71505-111">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="71505-111">\<issuerChannelBehaviors></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71505-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71505-112">Syntax</span></span>  
  
```xml  
<issuerChannelBehaviors>
  <add behaviorConfiguraton="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71505-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="71505-113">Attributes and Elements</span></span>  
 <span data-ttu-id="71505-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="71505-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71505-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="71505-115">Attributes</span></span>  
 <span data-ttu-id="71505-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="71505-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="71505-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="71505-117">Child Elements</span></span>  
  
|<span data-ttu-id="71505-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="71505-118">Element</span></span>|<span data-ttu-id="71505-119">Popis</span><span class="sxs-lookup"><span data-stu-id="71505-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71505-120">\<add></span><span class="sxs-lookup"><span data-stu-id="71505-120">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|<span data-ttu-id="71505-121">Přidá do kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="71505-121">Adds a behavior to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71505-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="71505-122">Parent Elements</span></span>  
  
|<span data-ttu-id="71505-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="71505-123">Element</span></span>|<span data-ttu-id="71505-124">Popis</span><span class="sxs-lookup"><span data-stu-id="71505-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71505-125">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="71505-125">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="71505-126">Určuje vlastní token pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="71505-126">Specifies a custom token used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71505-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71505-127">Remarks</span></span>  
 <span data-ttu-id="71505-128">Tento prvek, pokud žádný chování (jiné než chování, které zahrnují `<clientCredentials>` elementy) musí být použita ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="71505-128">Use this element when any behaviors (other than behaviors that include `<clientCredentials>` elements) must be used to communicate with a service.</span></span> <span data-ttu-id="71505-129">Například pokud [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) chování element musí být zahrnut.</span><span class="sxs-lookup"><span data-stu-id="71505-129">For example, if a [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) behavior element must be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71505-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71505-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="71505-131">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="71505-131">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="71505-132">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="71505-132">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="71505-133">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="71505-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="71505-134">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="71505-134">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="71505-135">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="71505-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="71505-136">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="71505-136">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="71505-137">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="71505-137">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="71505-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="71505-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
