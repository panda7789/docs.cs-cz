---
title: '&lt;security&gt; – &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7413820f1a1f38b3d533573715267df3b85c9d9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="33cae-102">&lt;security&gt; – &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="33cae-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="33cae-103">Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), včetně typu ověřování používají a zabezpečení používat pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="33cae-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="33cae-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="33cae-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="33cae-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="33cae-105">\<bindings></span></span>  
<span data-ttu-id="33cae-106">\<netpeerbinding – ></span><span class="sxs-lookup"><span data-stu-id="33cae-106">\<netPeerBinding></span></span>  
<span data-ttu-id="33cae-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="33cae-107">\<binding></span></span>  
<span data-ttu-id="33cae-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="33cae-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33cae-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33cae-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33cae-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="33cae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="33cae-111">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="33cae-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33cae-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="33cae-112">Attributes</span></span>  
  
|<span data-ttu-id="33cae-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="33cae-113">Attribute</span></span>|<span data-ttu-id="33cae-114">Popis</span><span class="sxs-lookup"><span data-stu-id="33cae-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33cae-115">režim</span><span class="sxs-lookup"><span data-stu-id="33cae-115">mode</span></span>|<span data-ttu-id="33cae-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="33cae-116">Optional.</span></span> <span data-ttu-id="33cae-117">Určuje typ zabezpečení používané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="33cae-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="33cae-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="33cae-118">The default value is `Message`.</span></span> <span data-ttu-id="33cae-119">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="33cae-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="33cae-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="33cae-120">mode Attribute</span></span>  
  
|<span data-ttu-id="33cae-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="33cae-121">Value</span></span>|<span data-ttu-id="33cae-122">Popis</span><span class="sxs-lookup"><span data-stu-id="33cae-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="33cae-123">Zpráva</span><span class="sxs-lookup"><span data-stu-id="33cae-123">Message</span></span>|<span data-ttu-id="33cae-124">Zabezpečení protokolu SOAP poskytuje ověřování, integrity a důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="33cae-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="33cae-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="33cae-125">None</span></span>|<span data-ttu-id="33cae-126">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="33cae-126">Security is disabled.</span></span>|  
|<span data-ttu-id="33cae-127">Přenos</span><span class="sxs-lookup"><span data-stu-id="33cae-127">Transport</span></span>|<span data-ttu-id="33cae-128">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="33cae-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="33cae-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="33cae-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="33cae-130">HTTPS poskytuje možnosti ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="33cae-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="33cae-131">Protokolu SOAP zprávy poskytují typy bohaté přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="33cae-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33cae-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="33cae-132">Child Elements</span></span>  
  
|<span data-ttu-id="33cae-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="33cae-133">Element</span></span>|<span data-ttu-id="33cae-134">Popis</span><span class="sxs-lookup"><span data-stu-id="33cae-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33cae-135">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="33cae-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="33cae-136">Definuje typ přenosu pro zabezpečené zprávy odeslané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="33cae-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="33cae-137">Tento element je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="33cae-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="33cae-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="33cae-138">Parent Elements</span></span>  
  
|<span data-ttu-id="33cae-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="33cae-139">Element</span></span>|<span data-ttu-id="33cae-140">Popis</span><span class="sxs-lookup"><span data-stu-id="33cae-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33cae-141">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="33cae-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="33cae-142">Definuje všechny možnosti vazby [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="33cae-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33cae-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33cae-143">Remarks</span></span>  
 <span data-ttu-id="33cae-144">Zabezpečení může být buď zpráva nebo přenos specifické.</span><span class="sxs-lookup"><span data-stu-id="33cae-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33cae-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="33cae-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="33cae-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="33cae-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="33cae-147">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="33cae-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="33cae-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="33cae-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="33cae-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="33cae-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="33cae-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="33cae-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="33cae-151">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="33cae-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
