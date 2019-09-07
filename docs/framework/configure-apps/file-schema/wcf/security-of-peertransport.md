---
title: <security> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399767"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="9e238-102">\<> zabezpečení > \<peerTransport</span><span class="sxs-lookup"><span data-stu-id="9e238-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="9e238-103">Obsahuje nastavení zabezpečení související s rovnocenným kanálem, včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="9e238-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="9e238-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9e238-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9e238-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9e238-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9e238-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="9e238-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="9e238-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9e238-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="9e238-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="9e238-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="9e238-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="9e238-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="9e238-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="9e238-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e238-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e238-111">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e238-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9e238-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9e238-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9e238-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e238-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="9e238-114">Attributes</span></span>  
  
|<span data-ttu-id="9e238-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="9e238-115">Attribute</span></span>|<span data-ttu-id="9e238-116">Popis</span><span class="sxs-lookup"><span data-stu-id="9e238-116">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="9e238-117">Určuje typ zabezpečení, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="9e238-117">Specifies the type of security to be applied.</span></span> <span data-ttu-id="9e238-118">Výchozí hodnota je zpráva.</span><span class="sxs-lookup"><span data-stu-id="9e238-118">The default value is Message.</span></span> <span data-ttu-id="9e238-119">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="9e238-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="9e238-120">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="9e238-120">mode Attribute</span></span>  
  
|<span data-ttu-id="9e238-121">Value</span><span class="sxs-lookup"><span data-stu-id="9e238-121">Value</span></span>|<span data-ttu-id="9e238-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9e238-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="9e238-123">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="9e238-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="9e238-124">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9e238-124">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="9e238-125">Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="9e238-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="9e238-126">Protokol HTTPS zajišťuje ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="9e238-126">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="9e238-127">Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="9e238-127">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e238-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9e238-128">Child Elements</span></span>  
  
|<span data-ttu-id="9e238-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="9e238-129">Element</span></span>|<span data-ttu-id="9e238-130">Popis</span><span class="sxs-lookup"><span data-stu-id="9e238-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e238-131">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="9e238-131">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="9e238-132">Definuje partnerský přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="9e238-132">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="9e238-133">Tento prvek má `clientCredentialType` atribut, který určuje pověření, která mají být použita při interakci se službou.</span><span class="sxs-lookup"><span data-stu-id="9e238-133">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="9e238-134">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9e238-134">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="9e238-135">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="9e238-135">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9e238-136">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9e238-136">Parent Elements</span></span>  
  
|<span data-ttu-id="9e238-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="9e238-137">Element</span></span>|<span data-ttu-id="9e238-138">Popis</span><span class="sxs-lookup"><span data-stu-id="9e238-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e238-139">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="9e238-139">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="9e238-140">Definuje partnerský přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="9e238-140">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e238-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e238-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9e238-142">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="9e238-142">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="9e238-143">Přenosy</span><span class="sxs-lookup"><span data-stu-id="9e238-143">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="9e238-144">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="9e238-144">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="9e238-145">Vazby</span><span class="sxs-lookup"><span data-stu-id="9e238-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9e238-146">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="9e238-146">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9e238-147">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="9e238-147">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="9e238-148">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9e238-148">\<customBinding></span></span>](custombinding.md)
