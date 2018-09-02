---
title: '&lt;peer&gt; elementu &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 9d63aaaa6404b791559d1288730098075f1fd8eb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43385473"
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="f0810-102">&lt;peer&gt; elementu &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="f0810-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="f0810-103">Určuje pověření používaný při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="f0810-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="f0810-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f0810-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f0810-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f0810-105">\<behaviors></span></span>  
<span data-ttu-id="f0810-106">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f0810-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="f0810-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f0810-107">\<behavior></span></span>  
<span data-ttu-id="f0810-108">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f0810-108">\<clientCredentials></span></span>  
<span data-ttu-id="f0810-109">\<sdílená ></span><span class="sxs-lookup"><span data-stu-id="f0810-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0810-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0810-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0810-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f0810-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f0810-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f0810-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0810-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f0810-113">Attributes</span></span>  
 <span data-ttu-id="f0810-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="f0810-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f0810-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f0810-115">Child Elements</span></span>  
  
|<span data-ttu-id="f0810-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="f0810-116">Element</span></span>|<span data-ttu-id="f0810-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f0810-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0810-118">\<certifikát ></span><span class="sxs-lookup"><span data-stu-id="f0810-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="f0810-119">Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="f0810-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="f0810-120">.</span><span class="sxs-lookup"><span data-stu-id="f0810-120">.</span></span>|  
|[<span data-ttu-id="f0810-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f0810-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="f0810-122">Určuje možnosti ověřování pro klienty sdílené.</span><span class="sxs-lookup"><span data-stu-id="f0810-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="f0810-123">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f0810-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="f0810-124">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="f0810-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0810-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f0810-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f0810-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="f0810-126">Element</span></span>|<span data-ttu-id="f0810-127">Popis</span><span class="sxs-lookup"><span data-stu-id="f0810-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0810-128">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="f0810-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="f0810-129">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="f0810-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0810-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0810-130">Remarks</span></span>  
 <span data-ttu-id="f0810-131">Tento prvek konfigurace určuje přihlašovací údaje, které partnerský uzel používá ke svému ověření do jiných uzlů v mřížce, jakož i nastavení ověřování, které partnerský uzel používá k ověřování další partnerské uzly.</span><span class="sxs-lookup"><span data-stu-id="f0810-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="f0810-132">Další informace najdete v tématu [ověřování zpráv Peer Channel](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) a [zabezpečení aplikace Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="f0810-132">For more information, see [Peer Channel Message Authentication](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0810-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0810-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="f0810-134">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="f0810-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="f0810-135">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="f0810-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="f0810-136">Ověřování zpráv protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="f0810-136">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="f0810-137">Vlastní ověřování protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="f0810-137">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="f0810-138">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="f0810-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="f0810-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f0810-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
