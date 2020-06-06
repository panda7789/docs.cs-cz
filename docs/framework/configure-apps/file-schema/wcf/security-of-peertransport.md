---
title: <security> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399767"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="70033-102">\<security> z \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="70033-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="70033-103">Obsahuje nastavení zabezpečení související s rovnocenným kanálem, včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="70033-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="70033-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70033-104">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70033-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="70033-105">Attributes and Elements</span></span>  
 <span data-ttu-id="70033-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="70033-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70033-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="70033-107">Attributes</span></span>  
  
|<span data-ttu-id="70033-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="70033-108">Attribute</span></span>|<span data-ttu-id="70033-109">Popis</span><span class="sxs-lookup"><span data-stu-id="70033-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="70033-110">Určuje typ zabezpečení, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="70033-110">Specifies the type of security to be applied.</span></span> <span data-ttu-id="70033-111">Výchozí hodnota je zpráva.</span><span class="sxs-lookup"><span data-stu-id="70033-111">The default value is Message.</span></span> <span data-ttu-id="70033-112">Tento atribut je typu <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="70033-112">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="70033-113">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="70033-113">mode Attribute</span></span>  
  
|<span data-ttu-id="70033-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="70033-114">Value</span></span>|<span data-ttu-id="70033-115">Description</span><span class="sxs-lookup"><span data-stu-id="70033-115">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="70033-116">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="70033-116">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="70033-117">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="70033-117">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="70033-118">Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="70033-118">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="70033-119">Protokol HTTPS zajišťuje ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="70033-119">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="70033-120">Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="70033-120">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70033-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="70033-121">Child Elements</span></span>  
  
|<span data-ttu-id="70033-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="70033-122">Element</span></span>|<span data-ttu-id="70033-123">Description</span><span class="sxs-lookup"><span data-stu-id="70033-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="70033-124">Definuje partnerský přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="70033-124">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="70033-125">Tento prvek má `clientCredentialType` atribut, který určuje pověření, která mají být použita při interakci se službou.</span><span class="sxs-lookup"><span data-stu-id="70033-125">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="70033-126">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="70033-126">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="70033-127">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="70033-127">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70033-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="70033-128">Parent Elements</span></span>  
  
|<span data-ttu-id="70033-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="70033-129">Element</span></span>|<span data-ttu-id="70033-130">Description</span><span class="sxs-lookup"><span data-stu-id="70033-130">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="70033-131">Definuje partnerský přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="70033-131">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="70033-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="70033-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="70033-133">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="70033-133">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="70033-134">Přenosy</span><span class="sxs-lookup"><span data-stu-id="70033-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="70033-135">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="70033-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="70033-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="70033-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="70033-137">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="70033-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="70033-138">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="70033-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
