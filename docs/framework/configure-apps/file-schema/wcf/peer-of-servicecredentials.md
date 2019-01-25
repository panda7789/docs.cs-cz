---
title: '&lt;peer&gt; – &lt;serviceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 132c001de02e223375453c91832f461b96b57dfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741254"
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="12c52-102">&lt;peer&gt; – &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="12c52-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="12c52-103">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="12c52-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="12c52-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="12c52-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="12c52-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="12c52-105">\<behaviors></span></span>  
<span data-ttu-id="12c52-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="12c52-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="12c52-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="12c52-107">\<behavior></span></span>  
<span data-ttu-id="12c52-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="12c52-108">\<serviceCredentials></span></span>  
<span data-ttu-id="12c52-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="12c52-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c52-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12c52-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12c52-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="12c52-111">Attributes and Elements</span></span>  
 <span data-ttu-id="12c52-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="12c52-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12c52-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="12c52-113">Attributes</span></span>  
 <span data-ttu-id="12c52-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="12c52-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="12c52-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="12c52-115">Child Elements</span></span>  
  
|<span data-ttu-id="12c52-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="12c52-116">Element</span></span>|<span data-ttu-id="12c52-117">Popis</span><span class="sxs-lookup"><span data-stu-id="12c52-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12c52-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="12c52-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="12c52-119">Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv služeb peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="12c52-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="12c52-120">.</span><span class="sxs-lookup"><span data-stu-id="12c52-120">.</span></span>|  
|[<span data-ttu-id="12c52-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="12c52-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="12c52-122">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="12c52-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="12c52-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="12c52-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="12c52-124">Určuje možnosti ověřování pro partnerské služby.</span><span class="sxs-lookup"><span data-stu-id="12c52-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12c52-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="12c52-125">Parent Elements</span></span>  
  
|<span data-ttu-id="12c52-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="12c52-126">Element</span></span>|<span data-ttu-id="12c52-127">Popis</span><span class="sxs-lookup"><span data-stu-id="12c52-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12c52-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="12c52-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="12c52-129">Určuje přihlašovací údaje pro ověřování služby a nastavení vztahující se k ověření přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="12c52-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12c52-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12c52-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="12c52-131">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="12c52-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="12c52-132">Ověřování zpráv protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="12c52-132">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [<span data-ttu-id="12c52-133">Vlastní ověřování protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="12c52-133">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [<span data-ttu-id="12c52-134">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="12c52-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="12c52-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="12c52-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
