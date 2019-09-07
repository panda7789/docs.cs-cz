---
title: <peer> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397642"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="86589-102">\<Partnerský > \<> ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="86589-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="86589-103">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="86589-103">Specifies the current credentials for a peer node.</span></span>  
  
<span data-ttu-id="86589-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="86589-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86589-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="86589-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="86589-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="86589-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="86589-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="86589-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="86589-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="86589-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="86589-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="86589-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="86589-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Partnerský >**</span><span class="sxs-lookup"><span data-stu-id="86589-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86589-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86589-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86589-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="86589-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86589-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="86589-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86589-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="86589-114">Attributes</span></span>  
 <span data-ttu-id="86589-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="86589-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="86589-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="86589-116">Child Elements</span></span>  
  
|<span data-ttu-id="86589-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="86589-117">Element</span></span>|<span data-ttu-id="86589-118">Popis</span><span class="sxs-lookup"><span data-stu-id="86589-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86589-119">\<> certifikátu</span><span class="sxs-lookup"><span data-stu-id="86589-119">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="86589-120">Určuje certifikát X. 509, který se použije pro podepisování a šifrování zpráv pro služby peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="86589-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="86589-121">.</span><span class="sxs-lookup"><span data-stu-id="86589-121">.</span></span>|  
|[<span data-ttu-id="86589-122">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="86589-122">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="86589-123">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="86589-123">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="86589-124">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="86589-124">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="86589-125">Určuje možnosti ověřování pro služby peer Service.</span><span class="sxs-lookup"><span data-stu-id="86589-125">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="86589-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="86589-126">Parent Elements</span></span>  
  
|<span data-ttu-id="86589-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="86589-127">Element</span></span>|<span data-ttu-id="86589-128">Popis</span><span class="sxs-lookup"><span data-stu-id="86589-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86589-129">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="86589-129">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="86589-130">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="86589-130">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86589-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86589-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="86589-132">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="86589-132">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="86589-133">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="86589-133">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="86589-134">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="86589-134">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="86589-135">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="86589-135">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="86589-136">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="86589-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
