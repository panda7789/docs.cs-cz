---
title: '&lt;security&gt; – &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 6b4fe62afad22de880fdaaefad0e719f29c63fd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553942"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="2f7ae-102">&lt;security&gt; – &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2f7ae-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="2f7ae-103">Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), včetně typ ověřování, který používá a zabezpečení pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="2f7ae-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2f7ae-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2f7ae-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="2f7ae-105">\<bindings></span></span>  
<span data-ttu-id="2f7ae-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="2f7ae-106">\<netPeerBinding></span></span>  
<span data-ttu-id="2f7ae-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2f7ae-107">\<binding></span></span>  
<span data-ttu-id="2f7ae-108">\<security></span><span class="sxs-lookup"><span data-stu-id="2f7ae-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f7ae-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f7ae-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f7ae-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2f7ae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2f7ae-111">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2f7ae-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f7ae-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2f7ae-112">Attributes</span></span>  
  
|<span data-ttu-id="2f7ae-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2f7ae-113">Attribute</span></span>|<span data-ttu-id="2f7ae-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2f7ae-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f7ae-115">režim</span><span class="sxs-lookup"><span data-stu-id="2f7ae-115">mode</span></span>|<span data-ttu-id="2f7ae-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-116">Optional.</span></span> <span data-ttu-id="2f7ae-117">Určuje typ zabezpečení používané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="2f7ae-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-118">The default value is `Message`.</span></span> <span data-ttu-id="2f7ae-119">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2f7ae-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="2f7ae-120">mode Attribute</span></span>  
  
|<span data-ttu-id="2f7ae-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2f7ae-121">Value</span></span>|<span data-ttu-id="2f7ae-122">Popis</span><span class="sxs-lookup"><span data-stu-id="2f7ae-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2f7ae-123">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2f7ae-123">Message</span></span>|<span data-ttu-id="2f7ae-124">Zabezpečení protokolu SOAP poskytuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="2f7ae-125">Žádná</span><span class="sxs-lookup"><span data-stu-id="2f7ae-125">None</span></span>|<span data-ttu-id="2f7ae-126">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-126">Security is disabled.</span></span>|  
|<span data-ttu-id="2f7ae-127">Přenos</span><span class="sxs-lookup"><span data-stu-id="2f7ae-127">Transport</span></span>|<span data-ttu-id="2f7ae-128">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="2f7ae-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="2f7ae-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="2f7ae-130">HTTPS zajišťuje ověřování a zachováním důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="2f7ae-131">Zprávy protokolu SOAP poskytuje typy bohaté přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f7ae-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2f7ae-132">Child Elements</span></span>  
  
|<span data-ttu-id="2f7ae-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="2f7ae-133">Element</span></span>|<span data-ttu-id="2f7ae-134">Popis</span><span class="sxs-lookup"><span data-stu-id="2f7ae-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f7ae-135">\<transport></span><span class="sxs-lookup"><span data-stu-id="2f7ae-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="2f7ae-136">Definuje typ přenosu pro zabezpečené zprávy odeslané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="2f7ae-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f7ae-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2f7ae-138">Parent Elements</span></span>  
  
|<span data-ttu-id="2f7ae-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="2f7ae-139">Element</span></span>|<span data-ttu-id="2f7ae-140">Popis</span><span class="sxs-lookup"><span data-stu-id="2f7ae-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f7ae-141">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2f7ae-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2f7ae-142">Definuje všechny vazby funkce [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2f7ae-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f7ae-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f7ae-143">Remarks</span></span>  
 <span data-ttu-id="2f7ae-144">Zabezpečení může být buď nebo přenosu specifické pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="2f7ae-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f7ae-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f7ae-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="2f7ae-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2f7ae-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2f7ae-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="2f7ae-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="2f7ae-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="2f7ae-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="2f7ae-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="2f7ae-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2f7ae-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2f7ae-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2f7ae-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2f7ae-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
