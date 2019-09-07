---
title: <peer><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400102"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="39fcc-102">\<Partnerský > \<elementu ClientCredentials ></span><span class="sxs-lookup"><span data-stu-id="39fcc-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="39fcc-103">Určuje přihlašovací údaje, které se používají při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="39fcc-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
<span data-ttu-id="39fcc-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="39fcc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="39fcc-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="39fcc-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="39fcc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="39fcc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="39fcc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="39fcc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="39fcc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="39fcc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="39fcc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="39fcc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="39fcc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Partnerský >**</span><span class="sxs-lookup"><span data-stu-id="39fcc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39fcc-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39fcc-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39fcc-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="39fcc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="39fcc-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="39fcc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39fcc-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="39fcc-114">Attributes</span></span>  
 <span data-ttu-id="39fcc-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="39fcc-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="39fcc-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="39fcc-116">Child Elements</span></span>  
  
|<span data-ttu-id="39fcc-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="39fcc-117">Element</span></span>|<span data-ttu-id="39fcc-118">Popis</span><span class="sxs-lookup"><span data-stu-id="39fcc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39fcc-119">\<> certifikátu</span><span class="sxs-lookup"><span data-stu-id="39fcc-119">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="39fcc-120">Určuje certifikát X. 509, který se použije pro podepisování a šifrování zpráv pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="39fcc-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="39fcc-121">.</span><span class="sxs-lookup"><span data-stu-id="39fcc-121">.</span></span>|  
|[<span data-ttu-id="39fcc-122">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="39fcc-122">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="39fcc-123">Určuje možnosti ověřování pro partnerské klienty.</span><span class="sxs-lookup"><span data-stu-id="39fcc-123">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="39fcc-124">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="39fcc-124">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="39fcc-125">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="39fcc-125">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39fcc-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="39fcc-126">Parent Elements</span></span>  
  
|<span data-ttu-id="39fcc-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="39fcc-127">Element</span></span>|<span data-ttu-id="39fcc-128">Popis</span><span class="sxs-lookup"><span data-stu-id="39fcc-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39fcc-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="39fcc-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="39fcc-130">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="39fcc-130">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39fcc-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39fcc-131">Remarks</span></span>  
 <span data-ttu-id="39fcc-132">Tento prvek konfigurace určuje přihlašovací údaje, které používá partnerský uzel k ověřování sebe sama na jiné uzly v síti, a také nastavení ověřování, které partnerský uzel používá k ověření jiných partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="39fcc-132">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="39fcc-133">Další informace najdete v tématu [ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) a [zabezpečení aplikací pro rovnocenné kanály](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="39fcc-133">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39fcc-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39fcc-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="39fcc-135">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="39fcc-135">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="39fcc-136">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="39fcc-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="39fcc-137">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="39fcc-137">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="39fcc-138">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="39fcc-138">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="39fcc-139">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="39fcc-139">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="39fcc-140">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="39fcc-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
