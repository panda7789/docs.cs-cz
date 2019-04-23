---
title: <transport> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 9b6f548515afbba5068659bd5c6f7f2b33f80cda
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076000"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="cfdc1-102">\<přenos > z \<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="cfdc1-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="cfdc1-103">Určuje typ spojení na zabezpečené zprávy odeslané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="cfdc1-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="cfdc1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cfdc1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cfdc1-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="cfdc1-105">\<bindings></span></span>  
<span data-ttu-id="cfdc1-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="cfdc1-106">\<customBinding></span></span>  
<span data-ttu-id="cfdc1-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="cfdc1-107">\<binding></span></span>  
<span data-ttu-id="cfdc1-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="cfdc1-108">\<peerTransport></span></span>  
<span data-ttu-id="cfdc1-109">\<security></span><span class="sxs-lookup"><span data-stu-id="cfdc1-109">\<security></span></span>  
<span data-ttu-id="cfdc1-110">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="cfdc1-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfdc1-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfdc1-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfdc1-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cfdc1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cfdc1-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cfdc1-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfdc1-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="cfdc1-114">Attributes</span></span>  
  
|<span data-ttu-id="cfdc1-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="cfdc1-115">Attribute</span></span>|<span data-ttu-id="cfdc1-116">Popis</span><span class="sxs-lookup"><span data-stu-id="cfdc1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cfdc1-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="cfdc1-117">credentialType</span></span>|<span data-ttu-id="cfdc1-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cfdc1-118">Optional.</span></span> <span data-ttu-id="cfdc1-119">Určuje typ pověření použitá k ověření zprávy odeslané s rovnocenný přenos.</span><span class="sxs-lookup"><span data-stu-id="cfdc1-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="cfdc1-120">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="cfdc1-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="cfdc1-121">credentialType atribut</span><span class="sxs-lookup"><span data-stu-id="cfdc1-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="cfdc1-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cfdc1-122">Value</span></span>|<span data-ttu-id="cfdc1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="cfdc1-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cfdc1-124">Certifikát</span><span class="sxs-lookup"><span data-stu-id="cfdc1-124">Certificate</span></span>|<span data-ttu-id="cfdc1-125">Ověřování rovnocenný kanál přenos vyžaduje x X509 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="cfdc1-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="cfdc1-126">Heslo</span><span class="sxs-lookup"><span data-stu-id="cfdc1-126">Password</span></span>|<span data-ttu-id="cfdc1-127">Ověřování rovnocenný kanál přenos vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="cfdc1-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfdc1-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cfdc1-128">Child Elements</span></span>  
 <span data-ttu-id="cfdc1-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="cfdc1-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cfdc1-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cfdc1-130">Parent Elements</span></span>  
  
|<span data-ttu-id="cfdc1-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="cfdc1-131">Element</span></span>|<span data-ttu-id="cfdc1-132">Popis</span><span class="sxs-lookup"><span data-stu-id="cfdc1-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfdc1-133">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="cfdc1-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="cfdc1-134">Definuje rovnocenný přenos nastavení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cfdc1-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfdc1-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfdc1-135">Remarks</span></span>  
 <span data-ttu-id="cfdc1-136">Tento element je nastavena, jen pokud atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) je nastavena na `Transport` nebo `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="cfdc1-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdc1-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfdc1-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="cfdc1-138">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="cfdc1-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="cfdc1-139">Přenosy</span><span class="sxs-lookup"><span data-stu-id="cfdc1-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="cfdc1-140">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="cfdc1-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="cfdc1-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="cfdc1-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="cfdc1-142">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="cfdc1-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cfdc1-143">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="cfdc1-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="cfdc1-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="cfdc1-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
