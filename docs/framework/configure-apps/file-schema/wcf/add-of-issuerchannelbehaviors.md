---
title: '&lt;add&gt; – &lt;issuerChannelBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 75531e8ed50ae89f379db23d228804612f4bfccb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="37ce6-102">&lt;add&gt; – &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="37ce6-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="37ce6-103">Přidá chování koncového bodu, který se má použít při komunikaci s služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="37ce6-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37ce6-104">Pokud obsahuje všechny chování koncového bodu [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="37ce6-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="37ce6-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="37ce6-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="37ce6-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="37ce6-106">\<behaviors></span></span>  
<span data-ttu-id="37ce6-107">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="37ce6-107">endpointBehaviors section</span></span>  
<span data-ttu-id="37ce6-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="37ce6-108">\<behavior></span></span>  
<span data-ttu-id="37ce6-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="37ce6-109">\<clientCredentials></span></span>  
<span data-ttu-id="37ce6-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="37ce6-110">\<issuedToken></span></span>  
<span data-ttu-id="37ce6-111">\<issuerChannelBehaviors > elementu</span><span class="sxs-lookup"><span data-stu-id="37ce6-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="37ce6-112">\<add></span><span class="sxs-lookup"><span data-stu-id="37ce6-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ce6-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37ce6-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37ce6-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="37ce6-114">Attributes and Elements</span></span>  
 <span data-ttu-id="37ce6-115">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="37ce6-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37ce6-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="37ce6-116">Attributes</span></span>  
  
|<span data-ttu-id="37ce6-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="37ce6-117">Attribute</span></span>|<span data-ttu-id="37ce6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="37ce6-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37ce6-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="37ce6-119">issuerAddress</span></span>|<span data-ttu-id="37ce6-120">Identifikátor URI vydavatel tokenu zabezpečení ke komunikaci s.</span><span class="sxs-lookup"><span data-stu-id="37ce6-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="37ce6-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="37ce6-121">behaviorConfiguration</span></span>|<span data-ttu-id="37ce6-122">Název koncový bod chování definované ve stejném souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="37ce6-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37ce6-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="37ce6-123">Child Elements</span></span>  
 <span data-ttu-id="37ce6-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="37ce6-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37ce6-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="37ce6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="37ce6-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="37ce6-126">Element</span></span>|<span data-ttu-id="37ce6-127">Popis</span><span class="sxs-lookup"><span data-stu-id="37ce6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37ce6-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="37ce6-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="37ce6-129">Obsahuje kolekce chování koncový bod klienta Windows Communication Foundation (WCF), který se má použít při komunikaci s určeným službám tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="37ce6-129">Contains a collection of Windows Communication Foundation (WCF) client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37ce6-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37ce6-130">Remarks</span></span>  
 <span data-ttu-id="37ce6-131">`issuerAddress` obsahuje identifikátor URI služby tokenů zabezpečení, který chce klienta ke komunikaci s.</span><span class="sxs-lookup"><span data-stu-id="37ce6-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="37ce6-132">`behaviorConfiguration` odkazuje na koncový bod chování, které aplikace používá v kanály vytvořen ve Windows Communication Foundation (WCF) k získání vystavené tokeny od služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="37ce6-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by Windows Communication Foundation (WCF) to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ce6-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="37ce6-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="37ce6-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="37ce6-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="37ce6-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="37ce6-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="37ce6-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="37ce6-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="37ce6-137">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="37ce6-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="37ce6-138">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="37ce6-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="37ce6-139">Postupy: Vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="37ce6-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="37ce6-140">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="37ce6-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="37ce6-141">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="37ce6-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="37ce6-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="37ce6-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
