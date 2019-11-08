---
title: <security> z <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738658"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="aaa52-102">> \<zabezpečení \<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="aaa52-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="aaa52-103">Definuje nastavení zabezpečení [\<netPeerTcpBinding >](netpeertcpbinding.md), včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="aaa52-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="aaa52-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aaa52-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aaa52-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="aaa52-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="aaa52-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="aaa52-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="aaa52-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="aaa52-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="aaa52-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="aaa52-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="aaa52-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení >**</span><span class="sxs-lookup"><span data-stu-id="aaa52-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa52-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaa52-110">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aaa52-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aaa52-111">Attributes and Elements</span></span>  
 <span data-ttu-id="aaa52-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aaa52-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aaa52-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="aaa52-113">Attributes</span></span>  
  
|<span data-ttu-id="aaa52-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="aaa52-114">Attribute</span></span>|<span data-ttu-id="aaa52-115">Popis</span><span class="sxs-lookup"><span data-stu-id="aaa52-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aaa52-116">režim</span><span class="sxs-lookup"><span data-stu-id="aaa52-116">mode</span></span>|<span data-ttu-id="aaa52-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="aaa52-117">Optional.</span></span> <span data-ttu-id="aaa52-118">Určuje typ zabezpečení, který používají partneři nakonfigurované s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="aaa52-118">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="aaa52-119">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="aaa52-119">The default value is `Message`.</span></span> <span data-ttu-id="aaa52-120">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="aaa52-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="aaa52-121">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="aaa52-121">mode Attribute</span></span>  
  
|<span data-ttu-id="aaa52-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aaa52-122">Value</span></span>|<span data-ttu-id="aaa52-123">Popis</span><span class="sxs-lookup"><span data-stu-id="aaa52-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aaa52-124">Zpráva</span><span class="sxs-lookup"><span data-stu-id="aaa52-124">Message</span></span>|<span data-ttu-id="aaa52-125">Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="aaa52-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="aaa52-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="aaa52-126">None</span></span>|<span data-ttu-id="aaa52-127">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="aaa52-127">Security is disabled.</span></span>|  
|<span data-ttu-id="aaa52-128">Přepravu</span><span class="sxs-lookup"><span data-stu-id="aaa52-128">Transport</span></span>|<span data-ttu-id="aaa52-129">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="aaa52-129">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="aaa52-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="aaa52-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="aaa52-131">Protokol HTTPS zajišťuje ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="aaa52-131">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="aaa52-132">Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="aaa52-132">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aaa52-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aaa52-133">Child Elements</span></span>  
  
|<span data-ttu-id="aaa52-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="aaa52-134">Element</span></span>|<span data-ttu-id="aaa52-135">Popis</span><span class="sxs-lookup"><span data-stu-id="aaa52-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aaa52-136">> přenos \<</span><span class="sxs-lookup"><span data-stu-id="aaa52-136">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="aaa52-137">Definuje typ přenosu pro zabezpečené zprávy odesílané partnerskými uzly nakonfigurovanými pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="aaa52-137">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="aaa52-138">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="aaa52-138">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aaa52-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aaa52-139">Parent Elements</span></span>  
  
|<span data-ttu-id="aaa52-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="aaa52-140">Element</span></span>|<span data-ttu-id="aaa52-141">Popis</span><span class="sxs-lookup"><span data-stu-id="aaa52-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aaa52-142">vazba \<</span><span class="sxs-lookup"><span data-stu-id="aaa52-142">\<binding></span></span>](bindings.md)|<span data-ttu-id="aaa52-143">Definuje všechny schopnosti vazby [\<netPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="aaa52-143">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaa52-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aaa52-144">Remarks</span></span>  
 <span data-ttu-id="aaa52-145">Zabezpečení může být specifické pro zprávy nebo pro přenos.</span><span class="sxs-lookup"><span data-stu-id="aaa52-145">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa52-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aaa52-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="aaa52-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="aaa52-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="aaa52-148">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="aaa52-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="aaa52-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="aaa52-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aaa52-150">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="aaa52-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="aaa52-151">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="aaa52-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="aaa52-152">vazba \<</span><span class="sxs-lookup"><span data-stu-id="aaa52-152">\<binding></span></span>](bindings.md)
