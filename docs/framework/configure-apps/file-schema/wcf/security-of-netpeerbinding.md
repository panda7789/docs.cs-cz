---
title: "&lt;security&gt; – &lt;netPeerBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: aac60b8502789e92c23072d139bf892ff055f9b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="09ba1-102">&lt;security&gt; – &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="09ba1-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="09ba1-103">Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), včetně typu ověřování používají a zabezpečení používat pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="09ba1-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="09ba1-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="09ba1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="09ba1-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="09ba1-105">\<bindings></span></span>  
<span data-ttu-id="09ba1-106">\<netpeerbinding – ></span><span class="sxs-lookup"><span data-stu-id="09ba1-106">\<netPeerBinding></span></span>  
<span data-ttu-id="09ba1-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="09ba1-107">\<binding></span></span>  
<span data-ttu-id="09ba1-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="09ba1-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ba1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09ba1-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09ba1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="09ba1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="09ba1-111">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="09ba1-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09ba1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="09ba1-112">Attributes</span></span>  
  
|<span data-ttu-id="09ba1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="09ba1-113">Attribute</span></span>|<span data-ttu-id="09ba1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="09ba1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09ba1-115">režim</span><span class="sxs-lookup"><span data-stu-id="09ba1-115">mode</span></span>|<span data-ttu-id="09ba1-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="09ba1-116">Optional.</span></span> <span data-ttu-id="09ba1-117">Určuje typ zabezpečení používané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="09ba1-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="09ba1-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="09ba1-118">The default value is `Message`.</span></span> <span data-ttu-id="09ba1-119">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="09ba1-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="09ba1-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="09ba1-120">mode Attribute</span></span>  
  
|<span data-ttu-id="09ba1-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="09ba1-121">Value</span></span>|<span data-ttu-id="09ba1-122">Popis</span><span class="sxs-lookup"><span data-stu-id="09ba1-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="09ba1-123">Zpráva</span><span class="sxs-lookup"><span data-stu-id="09ba1-123">Message</span></span>|<span data-ttu-id="09ba1-124">Zabezpečení protokolu SOAP poskytuje ověřování, integrity a důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="09ba1-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="09ba1-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="09ba1-125">None</span></span>|<span data-ttu-id="09ba1-126">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="09ba1-126">Security is disabled.</span></span>|  
|<span data-ttu-id="09ba1-127">Přenos</span><span class="sxs-lookup"><span data-stu-id="09ba1-127">Transport</span></span>|<span data-ttu-id="09ba1-128">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="09ba1-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="09ba1-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="09ba1-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="09ba1-130">HTTPS poskytuje možnosti ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="09ba1-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="09ba1-131">Protokolu SOAP zprávy poskytují typy bohaté přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="09ba1-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09ba1-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="09ba1-132">Child Elements</span></span>  
  
|<span data-ttu-id="09ba1-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="09ba1-133">Element</span></span>|<span data-ttu-id="09ba1-134">Popis</span><span class="sxs-lookup"><span data-stu-id="09ba1-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09ba1-135">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="09ba1-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="09ba1-136">Definuje typ přenosu pro zabezpečené zprávy odeslané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="09ba1-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="09ba1-137">Tento element je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="09ba1-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09ba1-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="09ba1-138">Parent Elements</span></span>  
  
|<span data-ttu-id="09ba1-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="09ba1-139">Element</span></span>|<span data-ttu-id="09ba1-140">Popis</span><span class="sxs-lookup"><span data-stu-id="09ba1-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09ba1-141">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="09ba1-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="09ba1-142">Definuje všechny možnosti vazby [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="09ba1-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09ba1-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09ba1-143">Remarks</span></span>  
 <span data-ttu-id="09ba1-144">Zabezpečení může být buď zpráva nebo přenos specifické.</span><span class="sxs-lookup"><span data-stu-id="09ba1-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ba1-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="09ba1-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="09ba1-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="09ba1-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="09ba1-147">Výběr typu pověření</span><span class="sxs-lookup"><span data-stu-id="09ba1-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="09ba1-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="09ba1-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="09ba1-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="09ba1-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="09ba1-150">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="09ba1-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="09ba1-151">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="09ba1-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
