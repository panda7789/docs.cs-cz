---
title: <peer><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 2f1cb5689125e2483a74dcac515beb07abbb7c70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934038"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="00fa0-102">\<Partnerský > \<elementu ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="00fa0-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="00fa0-103">Určuje přihlašovací údaje, které se používají při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="00fa0-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="00fa0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="00fa0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="00fa0-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="00fa0-105">\<behaviors></span></span>  
<span data-ttu-id="00fa0-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="00fa0-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="00fa0-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="00fa0-107">\<behavior></span></span>  
<span data-ttu-id="00fa0-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="00fa0-108">\<clientCredentials></span></span>  
<span data-ttu-id="00fa0-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="00fa0-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00fa0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00fa0-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00fa0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="00fa0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="00fa0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="00fa0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00fa0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="00fa0-113">Attributes</span></span>  
 <span data-ttu-id="00fa0-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="00fa0-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="00fa0-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="00fa0-115">Child Elements</span></span>  
  
|<span data-ttu-id="00fa0-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="00fa0-116">Element</span></span>|<span data-ttu-id="00fa0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="00fa0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00fa0-118">\<> certifikátu</span><span class="sxs-lookup"><span data-stu-id="00fa0-118">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="00fa0-119">Určuje certifikát X. 509, který se použije pro podepisování a šifrování zpráv pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="00fa0-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="00fa0-120">.</span><span class="sxs-lookup"><span data-stu-id="00fa0-120">.</span></span>|  
|[<span data-ttu-id="00fa0-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="00fa0-121">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="00fa0-122">Určuje možnosti ověřování pro partnerské klienty.</span><span class="sxs-lookup"><span data-stu-id="00fa0-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="00fa0-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="00fa0-123">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="00fa0-124">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="00fa0-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="00fa0-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="00fa0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="00fa0-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="00fa0-126">Element</span></span>|<span data-ttu-id="00fa0-127">Popis</span><span class="sxs-lookup"><span data-stu-id="00fa0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00fa0-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="00fa0-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="00fa0-129">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="00fa0-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00fa0-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00fa0-130">Remarks</span></span>  
 <span data-ttu-id="00fa0-131">Tento prvek konfigurace určuje přihlašovací údaje, které používá partnerský uzel k ověřování sebe sama na jiné uzly v síti, a také nastavení ověřování, které partnerský uzel používá k ověření jiných partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="00fa0-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="00fa0-132">Další informace najdete v tématu [ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) a [zabezpečení aplikací pro rovnocenné kanály](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="00fa0-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00fa0-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00fa0-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="00fa0-134">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="00fa0-134">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="00fa0-135">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="00fa0-135">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="00fa0-136">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="00fa0-136">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="00fa0-137">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="00fa0-137">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="00fa0-138">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="00fa0-138">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="00fa0-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="00fa0-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
