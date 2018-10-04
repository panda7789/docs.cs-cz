---
title: '&lt;security&gt; – &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
ms.openlocfilehash: 1d7ffaf72e34b700f4702b2e531afbf7e842de09
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48776849"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="a0d24-102">&lt;security&gt; – &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a0d24-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="a0d24-103">Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), včetně typ ověřování, který používá a zabezpečení pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="a0d24-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="a0d24-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a0d24-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a0d24-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a0d24-105">\<bindings></span></span>  
<span data-ttu-id="a0d24-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="a0d24-106">\<netPeerBinding></span></span>  
<span data-ttu-id="a0d24-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a0d24-107">\<binding></span></span>  
<span data-ttu-id="a0d24-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="a0d24-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d24-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0d24-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0d24-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a0d24-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a0d24-111">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a0d24-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0d24-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a0d24-112">Attributes</span></span>  
  
|<span data-ttu-id="a0d24-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a0d24-113">Attribute</span></span>|<span data-ttu-id="a0d24-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a0d24-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a0d24-115">režim</span><span class="sxs-lookup"><span data-stu-id="a0d24-115">mode</span></span>|<span data-ttu-id="a0d24-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a0d24-116">Optional.</span></span> <span data-ttu-id="a0d24-117">Určuje typ zabezpečení používané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="a0d24-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="a0d24-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="a0d24-118">The default value is `Message`.</span></span> <span data-ttu-id="a0d24-119">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="a0d24-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a0d24-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="a0d24-120">mode Attribute</span></span>  
  
|<span data-ttu-id="a0d24-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a0d24-121">Value</span></span>|<span data-ttu-id="a0d24-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a0d24-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a0d24-123">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a0d24-123">Message</span></span>|<span data-ttu-id="a0d24-124">Zabezpečení protokolu SOAP poskytuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="a0d24-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="a0d24-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="a0d24-125">None</span></span>|<span data-ttu-id="a0d24-126">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="a0d24-126">Security is disabled.</span></span>|  
|<span data-ttu-id="a0d24-127">Přenos</span><span class="sxs-lookup"><span data-stu-id="a0d24-127">Transport</span></span>|<span data-ttu-id="a0d24-128">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a0d24-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="a0d24-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a0d24-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="a0d24-130">HTTPS zajišťuje ověřování a zachováním důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="a0d24-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="a0d24-131">Zprávy protokolu SOAP poskytuje typy bohaté přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="a0d24-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0d24-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a0d24-132">Child Elements</span></span>  
  
|<span data-ttu-id="a0d24-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0d24-133">Element</span></span>|<span data-ttu-id="a0d24-134">Popis</span><span class="sxs-lookup"><span data-stu-id="a0d24-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0d24-135">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="a0d24-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="a0d24-136">Definuje typ přenosu pro zabezpečené zprávy odeslané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="a0d24-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="a0d24-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="a0d24-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0d24-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a0d24-138">Parent Elements</span></span>  
  
|<span data-ttu-id="a0d24-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0d24-139">Element</span></span>|<span data-ttu-id="a0d24-140">Popis</span><span class="sxs-lookup"><span data-stu-id="a0d24-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0d24-141">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a0d24-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a0d24-142">Definuje všechny vazby funkce [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a0d24-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0d24-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0d24-143">Remarks</span></span>  
 <span data-ttu-id="a0d24-144">Zabezpečení může být buď nebo přenosu specifické pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="a0d24-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d24-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0d24-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="a0d24-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a0d24-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a0d24-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="a0d24-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="a0d24-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="a0d24-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a0d24-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="a0d24-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a0d24-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a0d24-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="a0d24-151">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a0d24-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
