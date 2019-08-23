---
title: <peer> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 50415cb9b35d2a2053efa3313a415de518b7e36e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933776"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="4693c-102">\<Partnerský > \<> ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="4693c-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="4693c-103">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="4693c-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="4693c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4693c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4693c-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="4693c-105">\<behaviors></span></span>  
<span data-ttu-id="4693c-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="4693c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4693c-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="4693c-107">\<behavior></span></span>  
<span data-ttu-id="4693c-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="4693c-108">\<serviceCredentials></span></span>  
<span data-ttu-id="4693c-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="4693c-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4693c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4693c-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4693c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4693c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4693c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4693c-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4693c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="4693c-113">Attributes</span></span>  
 <span data-ttu-id="4693c-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="4693c-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4693c-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4693c-115">Child Elements</span></span>  
  
|<span data-ttu-id="4693c-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="4693c-116">Element</span></span>|<span data-ttu-id="4693c-117">Popis</span><span class="sxs-lookup"><span data-stu-id="4693c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4693c-118">\<> certifikátu</span><span class="sxs-lookup"><span data-stu-id="4693c-118">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="4693c-119">Určuje certifikát X. 509, který se použije pro podepisování a šifrování zpráv pro služby peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="4693c-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="4693c-120">.</span><span class="sxs-lookup"><span data-stu-id="4693c-120">.</span></span>|  
|[<span data-ttu-id="4693c-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="4693c-121">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="4693c-122">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="4693c-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="4693c-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="4693c-123">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="4693c-124">Určuje možnosti ověřování pro služby peer Service.</span><span class="sxs-lookup"><span data-stu-id="4693c-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4693c-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4693c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4693c-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="4693c-126">Element</span></span>|<span data-ttu-id="4693c-127">Popis</span><span class="sxs-lookup"><span data-stu-id="4693c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4693c-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="4693c-128">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="4693c-129">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="4693c-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4693c-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4693c-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="4693c-131">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="4693c-131">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="4693c-132">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4693c-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="4693c-133">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4693c-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="4693c-134">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="4693c-134">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="4693c-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4693c-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
