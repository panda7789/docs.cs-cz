---
title: <peer> z <clientCredentials> – Element
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 7074ee992755557d7e5503035c89bdbefd678792
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107234"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="76f21-102">\<sdílené > z \<clientCredentials > – Element</span><span class="sxs-lookup"><span data-stu-id="76f21-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="76f21-103">Určuje pověření používaný při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="76f21-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="76f21-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="76f21-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="76f21-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="76f21-105">\<behaviors></span></span>  
<span data-ttu-id="76f21-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="76f21-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="76f21-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="76f21-107">\<behavior></span></span>  
<span data-ttu-id="76f21-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="76f21-108">\<clientCredentials></span></span>  
<span data-ttu-id="76f21-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="76f21-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f21-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76f21-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76f21-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76f21-111">Attributes and Elements</span></span>  
 <span data-ttu-id="76f21-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76f21-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76f21-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="76f21-113">Attributes</span></span>  
 <span data-ttu-id="76f21-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="76f21-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="76f21-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76f21-115">Child Elements</span></span>  
  
|<span data-ttu-id="76f21-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="76f21-116">Element</span></span>|<span data-ttu-id="76f21-117">Popis</span><span class="sxs-lookup"><span data-stu-id="76f21-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76f21-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="76f21-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="76f21-119">Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="76f21-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="76f21-120">.</span><span class="sxs-lookup"><span data-stu-id="76f21-120">.</span></span>|  
|[<span data-ttu-id="76f21-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="76f21-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="76f21-122">Určuje možnosti ověřování pro klienty sdílené.</span><span class="sxs-lookup"><span data-stu-id="76f21-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="76f21-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="76f21-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="76f21-124">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="76f21-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76f21-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76f21-125">Parent Elements</span></span>  
  
|<span data-ttu-id="76f21-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="76f21-126">Element</span></span>|<span data-ttu-id="76f21-127">Popis</span><span class="sxs-lookup"><span data-stu-id="76f21-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76f21-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="76f21-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="76f21-129">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="76f21-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76f21-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76f21-130">Remarks</span></span>  
 <span data-ttu-id="76f21-131">Tento prvek konfigurace určuje přihlašovací údaje, které partnerský uzel používá ke svému ověření do jiných uzlů v mřížce, jakož i nastavení ověřování, které partnerský uzel používá k ověřování další partnerské uzly.</span><span class="sxs-lookup"><span data-stu-id="76f21-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="76f21-132">Další informace najdete v tématu [ověřování zpráv Peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) a [zabezpečení aplikace Peer Channel](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="76f21-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f21-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76f21-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="76f21-134">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="76f21-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="76f21-135">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="76f21-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- <span data-ttu-id="76f21-136">[Ověřování zpráv protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="76f21-136">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="76f21-137">[Vlastní ověřování protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="76f21-137">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="76f21-138">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="76f21-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="76f21-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="76f21-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
