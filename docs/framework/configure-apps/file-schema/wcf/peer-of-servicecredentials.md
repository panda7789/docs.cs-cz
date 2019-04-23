---
title: <peer> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: d726ab460141b1e373a1cabf770b8958f50319eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219145"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="3f9d6-102">\<sdílené > z \<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="3f9d6-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="3f9d6-103">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="3f9d6-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="3f9d6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3f9d6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3f9d6-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3f9d6-105">\<behaviors></span></span>  
<span data-ttu-id="3f9d6-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3f9d6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3f9d6-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3f9d6-107">\<behavior></span></span>  
<span data-ttu-id="3f9d6-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3f9d6-108">\<serviceCredentials></span></span>  
<span data-ttu-id="3f9d6-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="3f9d6-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f9d6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f9d6-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f9d6-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3f9d6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3f9d6-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3f9d6-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f9d6-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3f9d6-113">Attributes</span></span>  
 <span data-ttu-id="3f9d6-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="3f9d6-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f9d6-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3f9d6-115">Child Elements</span></span>  
  
|<span data-ttu-id="3f9d6-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="3f9d6-116">Element</span></span>|<span data-ttu-id="3f9d6-117">Popis</span><span class="sxs-lookup"><span data-stu-id="3f9d6-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f9d6-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="3f9d6-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="3f9d6-119">Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv služeb peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="3f9d6-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="3f9d6-120">.</span><span class="sxs-lookup"><span data-stu-id="3f9d6-120">.</span></span>|  
|[<span data-ttu-id="3f9d6-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="3f9d6-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="3f9d6-122">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="3f9d6-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="3f9d6-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="3f9d6-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="3f9d6-124">Určuje možnosti ověřování pro partnerské služby.</span><span class="sxs-lookup"><span data-stu-id="3f9d6-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f9d6-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3f9d6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3f9d6-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="3f9d6-126">Element</span></span>|<span data-ttu-id="3f9d6-127">Popis</span><span class="sxs-lookup"><span data-stu-id="3f9d6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f9d6-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3f9d6-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="3f9d6-129">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="3f9d6-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f9d6-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f9d6-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="3f9d6-131">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="3f9d6-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="3f9d6-132">[Ověřování zpráv protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3f9d6-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="3f9d6-133">[Vlastní ověřování protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3f9d6-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="3f9d6-134">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="3f9d6-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="3f9d6-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3f9d6-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
