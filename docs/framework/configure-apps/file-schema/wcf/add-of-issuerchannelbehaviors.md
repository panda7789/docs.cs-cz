---
title: <add> z <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 65c76cba696ae388d6184eaaa70a1f2f5a301e1c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271791"
---
# <a name="add-of-issuerchannelbehaviors"></a><span data-ttu-id="e5d79-102">\<add> of \<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="e5d79-102">\<add> of \<issuerChannelBehaviors></span></span>
<span data-ttu-id="e5d79-103">Přidá chování koncového bodu se použije při komunikaci se službou tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5d79-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5d79-104">Pokud jakékoliv chování koncového bodu obsahuje [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e5d79-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="e5d79-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e5d79-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e5d79-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e5d79-106">\<behaviors></span></span>  
<span data-ttu-id="e5d79-107">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="e5d79-107">endpointBehaviors section</span></span>  
<span data-ttu-id="e5d79-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="e5d79-108">\<behavior></span></span>  
<span data-ttu-id="e5d79-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="e5d79-109">\<clientCredentials></span></span>  
<span data-ttu-id="e5d79-110">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="e5d79-110">\<issuedToken></span></span>  
<span data-ttu-id="e5d79-111">\<issuerChannelBehaviors> Element</span><span class="sxs-lookup"><span data-stu-id="e5d79-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="e5d79-112">\<add></span><span class="sxs-lookup"><span data-stu-id="e5d79-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d79-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5d79-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"
     behaviorConfiguraton="string" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5d79-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e5d79-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e5d79-115">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e5d79-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5d79-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="e5d79-116">Attributes</span></span>  
  
|<span data-ttu-id="e5d79-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="e5d79-117">Attribute</span></span>|<span data-ttu-id="e5d79-118">Popis</span><span class="sxs-lookup"><span data-stu-id="e5d79-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5d79-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="e5d79-119">issuerAddress</span></span>|<span data-ttu-id="e5d79-120">Identifikátor URI vystavitele tokenu zabezpečení komunikovat.</span><span class="sxs-lookup"><span data-stu-id="e5d79-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="e5d79-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="e5d79-121">behaviorConfiguration</span></span>|<span data-ttu-id="e5d79-122">Název chování koncového bodu definované ve stejném souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e5d79-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5d79-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e5d79-123">Child Elements</span></span>  
 <span data-ttu-id="e5d79-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="e5d79-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5d79-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e5d79-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e5d79-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="e5d79-126">Element</span></span>|<span data-ttu-id="e5d79-127">Popis</span><span class="sxs-lookup"><span data-stu-id="e5d79-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5d79-128">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="e5d79-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="e5d79-129">Obsahuje kolekci chování koncového bodu klienta Windows Communication Foundation (WCF) se použije při komunikaci s určeným službám tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="e5d79-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5d79-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5d79-130">Remarks</span></span>  
 <span data-ttu-id="e5d79-131">`issuerAddress` obsahuje identifikátor URI, který chce komunikaci s klientem služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e5d79-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="e5d79-132">`behaviorConfiguration` odkazuje na chování koncového bodu, který aplikace používá v kanálech vytvořené technologií Windows Communication Foundation (WCF) Chcete-li získat od služby tokenů zabezpečení vydané tokeny.</span><span class="sxs-lookup"><span data-stu-id="e5d79-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d79-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5d79-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [<span data-ttu-id="e5d79-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="e5d79-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e5d79-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e5d79-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="e5d79-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="e5d79-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e5d79-137">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e5d79-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e5d79-138">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="e5d79-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="e5d79-139">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="e5d79-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="e5d79-140">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="e5d79-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [<span data-ttu-id="e5d79-141">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="e5d79-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e5d79-142">\<issuerChannelBehaviors></span><span class="sxs-lookup"><span data-stu-id="e5d79-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
