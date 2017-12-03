---
title: "&lt;add&gt; – &lt;issuerChannelBehaviors&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ea76a96597796b10c97ea57ca38c3bda453468c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a><span data-ttu-id="66529-102">&lt;add&gt; – &lt;issuerChannelBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="66529-102">&lt;add&gt; of &lt;issuerChannelBehaviors&gt;</span></span>
<span data-ttu-id="66529-103">Přidá chování koncového bodu, který se má použít při komunikaci s služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="66529-103">Adds an endpoint behavior to be used when communicating with an STS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66529-104">Pokud obsahuje všechny chování koncového bodu [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="66529-104">If any endpoint behavior contains a [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="66529-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="66529-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="66529-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="66529-106">\<behaviors></span></span>  
<span data-ttu-id="66529-107">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="66529-107">endpointBehaviors section</span></span>  
<span data-ttu-id="66529-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="66529-108">\<behavior></span></span>  
<span data-ttu-id="66529-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="66529-109">\<clientCredentials></span></span>  
<span data-ttu-id="66529-110">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="66529-110">\<issuedToken></span></span>  
<span data-ttu-id="66529-111">\<issuerChannelBehaviors > elementu</span><span class="sxs-lookup"><span data-stu-id="66529-111">\<issuerChannelBehaviors> Element</span></span>  
<span data-ttu-id="66529-112">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="66529-112">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66529-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66529-113">Syntax</span></span>  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66529-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="66529-114">Attributes and Elements</span></span>  
 <span data-ttu-id="66529-115">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="66529-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66529-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="66529-116">Attributes</span></span>  
  
|<span data-ttu-id="66529-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="66529-117">Attribute</span></span>|<span data-ttu-id="66529-118">Popis</span><span class="sxs-lookup"><span data-stu-id="66529-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66529-119">issuerAddress</span><span class="sxs-lookup"><span data-stu-id="66529-119">issuerAddress</span></span>|<span data-ttu-id="66529-120">Identifikátor URI vydavatel tokenu zabezpečení ke komunikaci s.</span><span class="sxs-lookup"><span data-stu-id="66529-120">The URI of the security token issuer to communicate with.</span></span>|  
|<span data-ttu-id="66529-121">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="66529-121">behaviorConfiguration</span></span>|<span data-ttu-id="66529-122">Název koncový bod chování definované ve stejném souboru konfigurace.</span><span class="sxs-lookup"><span data-stu-id="66529-122">The name of an endpoint behavior defined in the same configuration file.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66529-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="66529-123">Child Elements</span></span>  
 <span data-ttu-id="66529-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="66529-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66529-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="66529-125">Parent Elements</span></span>  
  
|<span data-ttu-id="66529-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="66529-126">Element</span></span>|<span data-ttu-id="66529-127">Popis</span><span class="sxs-lookup"><span data-stu-id="66529-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66529-128">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="66529-128">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|<span data-ttu-id="66529-129">Obsahuje kolekci [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] koncový bod chování klientů, který se má použít při komunikaci s určeným službám tokenu služby.</span><span class="sxs-lookup"><span data-stu-id="66529-129">Contains a collection of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client endpoint behaviors to be used when communicating with the specified Service Token Services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66529-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66529-130">Remarks</span></span>  
 <span data-ttu-id="66529-131">`issuerAddress`obsahuje identifikátor URI služby tokenů zabezpečení, který chce klienta ke komunikaci s.</span><span class="sxs-lookup"><span data-stu-id="66529-131">`issuerAddress` contains the URI of the Security Token Service that the client wants to communicate with.</span></span> <span data-ttu-id="66529-132">`behaviorConfiguration`odkazuje na koncový bod chování, které aplikace se používá v kanály vytvořené [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] získat vystavené tokeny od služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="66529-132">`behaviorConfiguration` points to an endpoint behavior that the application uses in the channels created by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] to get the issued tokens from the Security Token Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66529-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="66529-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [<span data-ttu-id="66529-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="66529-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="66529-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="66529-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="66529-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="66529-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="66529-137">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="66529-137">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="66529-138">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="66529-138">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="66529-139">Postupy: vytvoření federovaného klienta</span><span class="sxs-lookup"><span data-stu-id="66529-139">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="66529-140">Postupy: Konfigurace místního vystavitele</span><span class="sxs-lookup"><span data-stu-id="66529-140">How to: Configure a Local Issuer</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [<span data-ttu-id="66529-141">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="66529-141">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="66529-142">\<issuerChannelBehaviors ></span><span class="sxs-lookup"><span data-stu-id="66529-142">\<issuerChannelBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
