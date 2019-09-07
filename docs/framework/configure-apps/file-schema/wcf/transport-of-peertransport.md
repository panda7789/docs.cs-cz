---
title: <transport> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399293"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="050bd-102">\<> přenosu > \<peerTransport</span><span class="sxs-lookup"><span data-stu-id="050bd-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="050bd-103">Určuje typ přenosu zabezpečených zpráv odesílaných partnerskými uzly nakonfigurovanými pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="050bd-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
<span data-ttu-id="050bd-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="050bd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="050bd-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="050bd-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="050bd-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="050bd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="050bd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="050bd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="050bd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="050bd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="050bd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="050bd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="050bd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="050bd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)</span></span>\
<span data-ttu-id="050bd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> přenosu**</span><span class="sxs-lookup"><span data-stu-id="050bd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="050bd-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="050bd-112">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="050bd-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="050bd-113">Attributes and Elements</span></span>  
 <span data-ttu-id="050bd-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="050bd-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="050bd-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="050bd-115">Attributes</span></span>  
  
|<span data-ttu-id="050bd-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="050bd-116">Attribute</span></span>|<span data-ttu-id="050bd-117">Popis</span><span class="sxs-lookup"><span data-stu-id="050bd-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="050bd-118">credentialType</span><span class="sxs-lookup"><span data-stu-id="050bd-118">credentialType</span></span>|<span data-ttu-id="050bd-119">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="050bd-119">Optional.</span></span> <span data-ttu-id="050bd-120">Určuje typ přihlašovacích údajů, které se používají k ověření zpráv odesílaných pomocí partnerského přenosu.</span><span class="sxs-lookup"><span data-stu-id="050bd-120">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="050bd-121">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="050bd-121">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="050bd-122">credentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="050bd-122">credentialType Attribute</span></span>  
  
|<span data-ttu-id="050bd-123">Value</span><span class="sxs-lookup"><span data-stu-id="050bd-123">Value</span></span>|<span data-ttu-id="050bd-124">Popis</span><span class="sxs-lookup"><span data-stu-id="050bd-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="050bd-125">Certifikát</span><span class="sxs-lookup"><span data-stu-id="050bd-125">Certificate</span></span>|<span data-ttu-id="050bd-126">Ověřování přenosu rovnocenného kanálu vyžaduje certifikát x509.</span><span class="sxs-lookup"><span data-stu-id="050bd-126">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="050bd-127">Heslo</span><span class="sxs-lookup"><span data-stu-id="050bd-127">Password</span></span>|<span data-ttu-id="050bd-128">Ověření přenosu rovnocenného kanálu vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="050bd-128">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="050bd-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="050bd-129">Child Elements</span></span>  
 <span data-ttu-id="050bd-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="050bd-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="050bd-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="050bd-131">Parent Elements</span></span>  
  
|<span data-ttu-id="050bd-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="050bd-132">Element</span></span>|<span data-ttu-id="050bd-133">Popis</span><span class="sxs-lookup"><span data-stu-id="050bd-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="050bd-134">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="050bd-134">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="050bd-135">Definuje nastavení zabezpečení pro partnerský přenos.</span><span class="sxs-lookup"><span data-stu-id="050bd-135">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="050bd-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="050bd-136">Remarks</span></span>  
 <span data-ttu-id="050bd-137">Tento prvek je nastaven pouze v případě, že je atribut `Transport` `TransportWithMessageCredential` [ \<Mode > zabezpečení](security-of-peertransport.md) nastaven na nebo.</span><span class="sxs-lookup"><span data-stu-id="050bd-137">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050bd-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="050bd-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="050bd-139">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="050bd-139">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="050bd-140">Přenosy</span><span class="sxs-lookup"><span data-stu-id="050bd-140">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="050bd-141">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="050bd-141">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="050bd-142">Vazby</span><span class="sxs-lookup"><span data-stu-id="050bd-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="050bd-143">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="050bd-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="050bd-144">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="050bd-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="050bd-145">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="050bd-145">\<customBinding></span></span>](custombinding.md)
