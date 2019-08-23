---
title: <transport> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 5dbc55db25c0c49d72ec2cd8dd1041a3f8705d8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940637"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="72631-102">\<> přenosu > \<peerTransport</span><span class="sxs-lookup"><span data-stu-id="72631-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="72631-103">Určuje typ přenosu zabezpečených zpráv odesílaných partnerskými uzly nakonfigurovanými pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="72631-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="72631-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="72631-104">\<system.serviceModel></span></span>  
<span data-ttu-id="72631-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="72631-105">\<bindings></span></span>  
<span data-ttu-id="72631-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="72631-106">\<customBinding></span></span>  
<span data-ttu-id="72631-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="72631-107">\<binding></span></span>  
<span data-ttu-id="72631-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="72631-108">\<peerTransport></span></span>  
<span data-ttu-id="72631-109">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="72631-109">\<security></span></span>  
<span data-ttu-id="72631-110">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="72631-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72631-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72631-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72631-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="72631-112">Attributes and Elements</span></span>  
 <span data-ttu-id="72631-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="72631-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72631-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="72631-114">Attributes</span></span>  
  
|<span data-ttu-id="72631-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="72631-115">Attribute</span></span>|<span data-ttu-id="72631-116">Popis</span><span class="sxs-lookup"><span data-stu-id="72631-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="72631-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="72631-117">credentialType</span></span>|<span data-ttu-id="72631-118">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="72631-118">Optional.</span></span> <span data-ttu-id="72631-119">Určuje typ přihlašovacích údajů, které se používají k ověření zpráv odesílaných pomocí partnerského přenosu.</span><span class="sxs-lookup"><span data-stu-id="72631-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="72631-120">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="72631-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="72631-121">credentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="72631-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="72631-122">Value</span><span class="sxs-lookup"><span data-stu-id="72631-122">Value</span></span>|<span data-ttu-id="72631-123">Popis</span><span class="sxs-lookup"><span data-stu-id="72631-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="72631-124">Certifikát</span><span class="sxs-lookup"><span data-stu-id="72631-124">Certificate</span></span>|<span data-ttu-id="72631-125">Ověřování přenosu rovnocenného kanálu vyžaduje certifikát x509.</span><span class="sxs-lookup"><span data-stu-id="72631-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="72631-126">Heslo</span><span class="sxs-lookup"><span data-stu-id="72631-126">Password</span></span>|<span data-ttu-id="72631-127">Ověření přenosu rovnocenného kanálu vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="72631-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72631-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="72631-128">Child Elements</span></span>  
 <span data-ttu-id="72631-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="72631-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72631-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="72631-130">Parent Elements</span></span>  
  
|<span data-ttu-id="72631-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="72631-131">Element</span></span>|<span data-ttu-id="72631-132">Popis</span><span class="sxs-lookup"><span data-stu-id="72631-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72631-133">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="72631-133">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="72631-134">Definuje nastavení zabezpečení pro partnerský přenos.</span><span class="sxs-lookup"><span data-stu-id="72631-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72631-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72631-135">Remarks</span></span>  
 <span data-ttu-id="72631-136">Tento prvek je nastaven pouze v případě, že je atribut `Transport` `TransportWithMessageCredential` [ \<Mode > zabezpečení](security-of-peertransport.md) nastaven na nebo.</span><span class="sxs-lookup"><span data-stu-id="72631-136">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72631-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72631-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="72631-138">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="72631-138">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="72631-139">Přenosy</span><span class="sxs-lookup"><span data-stu-id="72631-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="72631-140">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="72631-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="72631-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="72631-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="72631-142">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="72631-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="72631-143">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="72631-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="72631-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="72631-144">\<customBinding></span></span>](custombinding.md)
