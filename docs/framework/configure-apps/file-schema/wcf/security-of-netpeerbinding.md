---
title: <security> z <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936630"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="992b0-102">\<> zabezpečení > \<netPeerBinding</span><span class="sxs-lookup"><span data-stu-id="992b0-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="992b0-103">Definuje nastavení [ \<zabezpečení NetPeerTcpBinding >](netpeertcpbinding.md), včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="992b0-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="992b0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="992b0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="992b0-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="992b0-105">\<bindings></span></span>  
<span data-ttu-id="992b0-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="992b0-106">\<netPeerBinding></span></span>  
<span data-ttu-id="992b0-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="992b0-107">\<binding></span></span>  
<span data-ttu-id="992b0-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="992b0-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="992b0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="992b0-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="992b0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="992b0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="992b0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="992b0-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="992b0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="992b0-112">Attributes</span></span>  
  
|<span data-ttu-id="992b0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="992b0-113">Attribute</span></span>|<span data-ttu-id="992b0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="992b0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="992b0-115">režim</span><span class="sxs-lookup"><span data-stu-id="992b0-115">mode</span></span>|<span data-ttu-id="992b0-116">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="992b0-116">Optional.</span></span> <span data-ttu-id="992b0-117">Určuje typ zabezpečení, který používají partneři nakonfigurované s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="992b0-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="992b0-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="992b0-118">The default value is `Message`.</span></span> <span data-ttu-id="992b0-119">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="992b0-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="992b0-120">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="992b0-120">mode Attribute</span></span>  
  
|<span data-ttu-id="992b0-121">Value</span><span class="sxs-lookup"><span data-stu-id="992b0-121">Value</span></span>|<span data-ttu-id="992b0-122">Popis</span><span class="sxs-lookup"><span data-stu-id="992b0-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="992b0-123">Message</span><span class="sxs-lookup"><span data-stu-id="992b0-123">Message</span></span>|<span data-ttu-id="992b0-124">Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="992b0-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="992b0-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="992b0-125">None</span></span>|<span data-ttu-id="992b0-126">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="992b0-126">Security is disabled.</span></span>|  
|<span data-ttu-id="992b0-127">Přepravu</span><span class="sxs-lookup"><span data-stu-id="992b0-127">Transport</span></span>|<span data-ttu-id="992b0-128">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="992b0-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="992b0-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="992b0-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="992b0-130">Protokol HTTPS zajišťuje ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="992b0-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="992b0-131">Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="992b0-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="992b0-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="992b0-132">Child Elements</span></span>  
  
|<span data-ttu-id="992b0-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="992b0-133">Element</span></span>|<span data-ttu-id="992b0-134">Popis</span><span class="sxs-lookup"><span data-stu-id="992b0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="992b0-135">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="992b0-135">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="992b0-136">Definuje typ přenosu pro zabezpečené zprávy odesílané partnerskými uzly nakonfigurovanými pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="992b0-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="992b0-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="992b0-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="992b0-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="992b0-138">Parent Elements</span></span>  
  
|<span data-ttu-id="992b0-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="992b0-139">Element</span></span>|<span data-ttu-id="992b0-140">Popis</span><span class="sxs-lookup"><span data-stu-id="992b0-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="992b0-141">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="992b0-141">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="992b0-142">Definuje všechny schopnosti [ \<vazby NetPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="992b0-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="992b0-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="992b0-143">Remarks</span></span>  
 <span data-ttu-id="992b0-144">Zabezpečení může být specifické pro zprávy nebo pro přenos.</span><span class="sxs-lookup"><span data-stu-id="992b0-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992b0-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="992b0-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="992b0-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="992b0-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="992b0-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="992b0-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="992b0-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="992b0-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="992b0-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="992b0-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="992b0-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="992b0-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="992b0-151">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="992b0-151">\<binding></span></span>](../../../misc/binding.md)
