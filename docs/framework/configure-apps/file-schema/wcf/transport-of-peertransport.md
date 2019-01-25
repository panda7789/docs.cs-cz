---
title: '&lt;transport&gt; – &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: d02bb1cb4c20ab7dc482001ea7ce21180394eee7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716580"
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="46500-102">&lt;transport&gt; – &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="46500-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="46500-103">Určuje typ spojení na zabezpečené zprávy odeslané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="46500-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="46500-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="46500-104">\<system.serviceModel></span></span>  
<span data-ttu-id="46500-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="46500-105">\<bindings></span></span>  
<span data-ttu-id="46500-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="46500-106">\<customBinding></span></span>  
<span data-ttu-id="46500-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="46500-107">\<binding></span></span>  
<span data-ttu-id="46500-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="46500-108">\<peerTransport></span></span>  
<span data-ttu-id="46500-109">\<security></span><span class="sxs-lookup"><span data-stu-id="46500-109">\<security></span></span>  
<span data-ttu-id="46500-110">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="46500-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46500-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46500-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46500-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="46500-112">Attributes and Elements</span></span>  
 <span data-ttu-id="46500-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="46500-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46500-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="46500-114">Attributes</span></span>  
  
|<span data-ttu-id="46500-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="46500-115">Attribute</span></span>|<span data-ttu-id="46500-116">Popis</span><span class="sxs-lookup"><span data-stu-id="46500-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46500-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="46500-117">credentialType</span></span>|<span data-ttu-id="46500-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="46500-118">Optional.</span></span> <span data-ttu-id="46500-119">Určuje typ pověření použitá k ověření zprávy odeslané s rovnocenný přenos.</span><span class="sxs-lookup"><span data-stu-id="46500-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="46500-120">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="46500-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="46500-121">credentialType atribut</span><span class="sxs-lookup"><span data-stu-id="46500-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="46500-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="46500-122">Value</span></span>|<span data-ttu-id="46500-123">Popis</span><span class="sxs-lookup"><span data-stu-id="46500-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="46500-124">Certifikát</span><span class="sxs-lookup"><span data-stu-id="46500-124">Certificate</span></span>|<span data-ttu-id="46500-125">Ověřování rovnocenný kanál přenos vyžaduje x X509 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="46500-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="46500-126">Heslo</span><span class="sxs-lookup"><span data-stu-id="46500-126">Password</span></span>|<span data-ttu-id="46500-127">Ověřování rovnocenný kanál přenos vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="46500-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46500-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="46500-128">Child Elements</span></span>  
 <span data-ttu-id="46500-129">Žádná</span><span class="sxs-lookup"><span data-stu-id="46500-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46500-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="46500-130">Parent Elements</span></span>  
  
|<span data-ttu-id="46500-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="46500-131">Element</span></span>|<span data-ttu-id="46500-132">Popis</span><span class="sxs-lookup"><span data-stu-id="46500-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46500-133">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="46500-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="46500-134">Definuje rovnocenný přenos nastavení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="46500-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46500-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46500-135">Remarks</span></span>  
 <span data-ttu-id="46500-136">Tento element je nastavena, jen pokud atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) je nastavena na `Transport` nebo `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="46500-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46500-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46500-137">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="46500-138">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="46500-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="46500-139">Přenosy</span><span class="sxs-lookup"><span data-stu-id="46500-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="46500-140">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="46500-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="46500-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="46500-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="46500-142">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="46500-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="46500-143">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="46500-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="46500-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="46500-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
