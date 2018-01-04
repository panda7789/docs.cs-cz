---
title: "&lt;peer&gt; – &lt;serviceCredentials&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d04c6121c5d106f5877517e9f72d1b533480dfb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="f18c2-102">&lt;peer&gt; – &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="f18c2-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="f18c2-103">Určuje, že aktuální přihlašovací údaje pro uzel sdílené.</span><span class="sxs-lookup"><span data-stu-id="f18c2-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="f18c2-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f18c2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f18c2-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f18c2-105">\<behaviors></span></span>  
<span data-ttu-id="f18c2-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f18c2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f18c2-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f18c2-107">\<behavior></span></span>  
<span data-ttu-id="f18c2-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f18c2-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f18c2-109">\<sdílené ></span><span class="sxs-lookup"><span data-stu-id="f18c2-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18c2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f18c2-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f18c2-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f18c2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f18c2-112">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f18c2-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f18c2-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f18c2-113">Attributes</span></span>  
 <span data-ttu-id="f18c2-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="f18c2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f18c2-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f18c2-115">Child Elements</span></span>  
  
|<span data-ttu-id="f18c2-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="f18c2-116">Element</span></span>|<span data-ttu-id="f18c2-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f18c2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18c2-118">\<certifikátu ></span><span class="sxs-lookup"><span data-stu-id="f18c2-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="f18c2-119">Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv pro služby peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="f18c2-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="f18c2-120">.</span><span class="sxs-lookup"><span data-stu-id="f18c2-120">.</span></span>|  
|[<span data-ttu-id="f18c2-121">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f18c2-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="f18c2-122">Určuje možnosti ověřování pro odesílatelé zpráv.</span><span class="sxs-lookup"><span data-stu-id="f18c2-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="f18c2-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="f18c2-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="f18c2-124">Určuje možnosti ověřování pro služby peer.</span><span class="sxs-lookup"><span data-stu-id="f18c2-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f18c2-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f18c2-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f18c2-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="f18c2-126">Element</span></span>|<span data-ttu-id="f18c2-127">Popis</span><span class="sxs-lookup"><span data-stu-id="f18c2-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18c2-128">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f18c2-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="f18c2-129">Určuje pověření, která se použije v ověřování služby a nastavení související s ověření pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="f18c2-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f18c2-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f18c2-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="f18c2-131">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="f18c2-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="f18c2-132">Ověřování zpráv rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="f18c2-132">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="f18c2-133">Vlastní ověřování rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="f18c2-133">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="f18c2-134">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="f18c2-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="f18c2-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f18c2-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
