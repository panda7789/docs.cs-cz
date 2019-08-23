---
title: <security> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: bdd3b236c9bae198f8027c4ca0c0fa5b70d30342
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936642"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="03303-102">\<> zabezpečení > \<peerTransport</span><span class="sxs-lookup"><span data-stu-id="03303-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="03303-103">Obsahuje nastavení zabezpečení související s rovnocenným kanálem, včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="03303-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="03303-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="03303-104">\<system.serviceModel></span></span>  
<span data-ttu-id="03303-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="03303-105">\<bindings></span></span>  
<span data-ttu-id="03303-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="03303-106">\<customBinding></span></span>  
<span data-ttu-id="03303-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="03303-107">\<binding></span></span>  
<span data-ttu-id="03303-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="03303-108">\<peerTransport></span></span>  
<span data-ttu-id="03303-109">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="03303-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03303-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03303-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03303-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03303-111">Attributes and Elements</span></span>  
 <span data-ttu-id="03303-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03303-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03303-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="03303-113">Attributes</span></span>  
  
|<span data-ttu-id="03303-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="03303-114">Attribute</span></span>|<span data-ttu-id="03303-115">Popis</span><span class="sxs-lookup"><span data-stu-id="03303-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="03303-116">Určuje typ zabezpečení, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="03303-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="03303-117">Výchozí hodnota je zpráva.</span><span class="sxs-lookup"><span data-stu-id="03303-117">The default value is Message.</span></span> <span data-ttu-id="03303-118">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="03303-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="03303-119">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="03303-119">mode Attribute</span></span>  
  
|<span data-ttu-id="03303-120">Value</span><span class="sxs-lookup"><span data-stu-id="03303-120">Value</span></span>|<span data-ttu-id="03303-121">Popis</span><span class="sxs-lookup"><span data-stu-id="03303-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="03303-122">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="03303-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="03303-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="03303-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="03303-124">Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="03303-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="03303-125">Protokol HTTPS zajišťuje ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="03303-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="03303-126">Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="03303-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03303-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03303-127">Child Elements</span></span>  
  
|<span data-ttu-id="03303-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="03303-128">Element</span></span>|<span data-ttu-id="03303-129">Popis</span><span class="sxs-lookup"><span data-stu-id="03303-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03303-130">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="03303-130">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="03303-131">Definuje partnerský přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="03303-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="03303-132">Tento prvek má `clientCredentialType` atribut, který určuje pověření, která mají být použita při interakci se službou.</span><span class="sxs-lookup"><span data-stu-id="03303-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="03303-133">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="03303-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="03303-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="03303-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03303-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03303-135">Parent Elements</span></span>  
  
|<span data-ttu-id="03303-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="03303-136">Element</span></span>|<span data-ttu-id="03303-137">Popis</span><span class="sxs-lookup"><span data-stu-id="03303-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03303-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="03303-138">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="03303-139">Definuje partnerský přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="03303-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03303-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03303-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="03303-141">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="03303-141">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="03303-142">Přenosy</span><span class="sxs-lookup"><span data-stu-id="03303-142">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="03303-143">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="03303-143">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="03303-144">Vazby</span><span class="sxs-lookup"><span data-stu-id="03303-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="03303-145">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="03303-145">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="03303-146">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="03303-146">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="03303-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="03303-147">\<customBinding></span></span>](custombinding.md)
