---
title: <peer> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 2090e79e6affe8ade6e2e52b94d2c4e1dafe8fa1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266023"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="1e500-102">\<sdílené > z \<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="1e500-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="1e500-103">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="1e500-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="1e500-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1e500-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1e500-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1e500-105">\<behaviors></span></span>  
<span data-ttu-id="1e500-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1e500-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1e500-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="1e500-107">\<behavior></span></span>  
<span data-ttu-id="1e500-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1e500-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1e500-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="1e500-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e500-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e500-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e500-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1e500-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1e500-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1e500-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e500-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1e500-113">Attributes</span></span>  
 <span data-ttu-id="1e500-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="1e500-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e500-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1e500-115">Child Elements</span></span>  
  
|<span data-ttu-id="1e500-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="1e500-116">Element</span></span>|<span data-ttu-id="1e500-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1e500-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e500-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="1e500-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="1e500-119">Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv služeb peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="1e500-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="1e500-120">.</span><span class="sxs-lookup"><span data-stu-id="1e500-120">.</span></span>|  
|[<span data-ttu-id="1e500-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="1e500-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="1e500-122">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="1e500-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="1e500-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="1e500-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="1e500-124">Určuje možnosti ověřování pro partnerské služby.</span><span class="sxs-lookup"><span data-stu-id="1e500-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e500-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1e500-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1e500-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="1e500-126">Element</span></span>|<span data-ttu-id="1e500-127">Popis</span><span class="sxs-lookup"><span data-stu-id="1e500-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e500-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1e500-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="1e500-129">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="1e500-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e500-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e500-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="1e500-131">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="1e500-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="1e500-132">Ověřování zpráv protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="1e500-132">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [<span data-ttu-id="1e500-133">Vlastní ověřování protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="1e500-133">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [<span data-ttu-id="1e500-134">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="1e500-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="1e500-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="1e500-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
