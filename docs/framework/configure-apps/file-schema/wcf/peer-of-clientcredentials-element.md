---
title: '&lt;peer&gt; elementu &lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: accd6c261a393da3ffcffd261d6603d20b8fcb3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="7514b-102">&lt;peer&gt; elementu &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="7514b-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="7514b-103">Určuje pověření použitá při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="7514b-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="7514b-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7514b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7514b-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7514b-105">\<behaviors></span></span>  
<span data-ttu-id="7514b-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7514b-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7514b-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7514b-107">\<behavior></span></span>  
<span data-ttu-id="7514b-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="7514b-108">\<clientCredentials></span></span>  
<span data-ttu-id="7514b-109">\<sdílené ></span><span class="sxs-lookup"><span data-stu-id="7514b-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7514b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7514b-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7514b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7514b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7514b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7514b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7514b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="7514b-113">Attributes</span></span>  
 <span data-ttu-id="7514b-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="7514b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7514b-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7514b-115">Child Elements</span></span>  
  
|<span data-ttu-id="7514b-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="7514b-116">Element</span></span>|<span data-ttu-id="7514b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7514b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7514b-118">\<certifikátu ></span><span class="sxs-lookup"><span data-stu-id="7514b-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="7514b-119">Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="7514b-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="7514b-120">.</span><span class="sxs-lookup"><span data-stu-id="7514b-120">.</span></span>|  
|[<span data-ttu-id="7514b-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7514b-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="7514b-122">Určuje možnosti ověřování pro klienty sdílené.</span><span class="sxs-lookup"><span data-stu-id="7514b-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="7514b-123">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7514b-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="7514b-124">Určuje možnosti ověřování pro odesílatelé zpráv.</span><span class="sxs-lookup"><span data-stu-id="7514b-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7514b-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7514b-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7514b-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="7514b-126">Element</span></span>|<span data-ttu-id="7514b-127">Popis</span><span class="sxs-lookup"><span data-stu-id="7514b-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7514b-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="7514b-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="7514b-129">Určuje pověření použitá k ověření klienta pro službu.</span><span class="sxs-lookup"><span data-stu-id="7514b-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7514b-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7514b-130">Remarks</span></span>  
 <span data-ttu-id="7514b-131">Tento element konfigurace Určuje pověření, které používá sdílené uzlu ke svému ověření do dalších uzlů v mřížce, jakož i nastavení ověřování, které uzlem sdílené používá k ověření dalších partnerské uzly.</span><span class="sxs-lookup"><span data-stu-id="7514b-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="7514b-132">Další informace najdete v tématu [ověřování zpráv kanál sdílené](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) a [zabezpečení aplikací kanálu sdílené](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="7514b-132">For more information, see [Peer Channel Message Authentication](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7514b-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="7514b-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="7514b-134">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="7514b-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="7514b-135">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="7514b-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="7514b-136">Ověřování zpráv rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="7514b-136">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="7514b-137">Vlastní ověřování rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="7514b-137">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="7514b-138">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="7514b-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="7514b-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7514b-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
