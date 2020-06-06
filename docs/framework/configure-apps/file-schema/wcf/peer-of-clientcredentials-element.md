---
title: <peer><clientCredentials>elementu
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400102"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="f2ca6-102">\<peer>\<clientCredentials>elementu</span><span class="sxs-lookup"><span data-stu-id="f2ca6-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="f2ca6-103">Určuje přihlašovací údaje, které se používají při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="f2ca6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2ca6-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2ca6-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f2ca6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f2ca6-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2ca6-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f2ca6-107">Attributes</span></span>  
 <span data-ttu-id="f2ca6-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="f2ca6-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2ca6-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f2ca6-109">Child Elements</span></span>  
  
|<span data-ttu-id="f2ca6-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="f2ca6-110">Element</span></span>|<span data-ttu-id="f2ca6-111">Description</span><span class="sxs-lookup"><span data-stu-id="f2ca6-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="f2ca6-112">Určuje certifikát X. 509, který se použije pro podepisování a šifrování zpráv pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="f2ca6-113">.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-113">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="f2ca6-114">Určuje možnosti ověřování pro partnerské klienty.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-114">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="f2ca6-115">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-115">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2ca6-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f2ca6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f2ca6-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="f2ca6-117">Element</span></span>|<span data-ttu-id="f2ca6-118">Description</span><span class="sxs-lookup"><span data-stu-id="f2ca6-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="f2ca6-119">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-119">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2ca6-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2ca6-120">Remarks</span></span>  
 <span data-ttu-id="f2ca6-121">Tento prvek konfigurace určuje přihlašovací údaje, které používá partnerský uzel k ověřování sebe sama na jiné uzly v síti, a také nastavení ověřování, které partnerský uzel používá k ověření jiných partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="f2ca6-121">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="f2ca6-122">Další informace najdete v tématu [ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) a [zabezpečení aplikací pro rovnocenné kanály](../../../wcf/feature-details/securing-peer-channel-applications.md).</span><span class="sxs-lookup"><span data-stu-id="f2ca6-122">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ca6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2ca6-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="f2ca6-124">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="f2ca6-124">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="f2ca6-125">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="f2ca6-125">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="f2ca6-126">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f2ca6-126">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f2ca6-127">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f2ca6-127">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f2ca6-128">Zabezpečení aplikací rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="f2ca6-128">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="f2ca6-129">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f2ca6-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
