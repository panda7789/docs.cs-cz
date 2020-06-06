---
title: <peer> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397642"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="a6e3f-102">\<peer> z \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a6e3f-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="a6e3f-103">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="a6e3f-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="a6e3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6e3f-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6e3f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a6e3f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a6e3f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a6e3f-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6e3f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6e3f-107">Attributes</span></span>  
 <span data-ttu-id="a6e3f-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="a6e3f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a6e3f-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6e3f-109">Child Elements</span></span>  
  
|<span data-ttu-id="a6e3f-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6e3f-110">Element</span></span>|<span data-ttu-id="a6e3f-111">Description</span><span class="sxs-lookup"><span data-stu-id="a6e3f-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="a6e3f-112">Určuje certifikát X. 509, který se použije pro podepisování a šifrování zpráv pro služby peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="a6e3f-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="a6e3f-113">.</span><span class="sxs-lookup"><span data-stu-id="a6e3f-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="a6e3f-114">Určuje možnosti ověřování pro odesílatele zpráv.</span><span class="sxs-lookup"><span data-stu-id="a6e3f-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="a6e3f-115">Určuje možnosti ověřování pro služby peer Service.</span><span class="sxs-lookup"><span data-stu-id="a6e3f-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6e3f-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a6e3f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a6e3f-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6e3f-117">Element</span></span>|<span data-ttu-id="a6e3f-118">Description</span><span class="sxs-lookup"><span data-stu-id="a6e3f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="a6e3f-119">Určuje přihlašovací údaje, které se mají použít při ověřování služby, a nastavení související s ověřením přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="a6e3f-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6e3f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6e3f-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="a6e3f-121">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="a6e3f-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="a6e3f-122">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a6e3f-122">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="a6e3f-123">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a6e3f-123">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="a6e3f-124">Zabezpečení aplikací rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="a6e3f-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="a6e3f-125">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a6e3f-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
