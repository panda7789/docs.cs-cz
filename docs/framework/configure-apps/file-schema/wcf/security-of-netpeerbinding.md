---
title: <security> z <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738658"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="596f1-102">\<security> z \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="596f1-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="596f1-103">Definuje nastavení zabezpečení [\<netPeerTcpBinding>](netpeertcpbinding.md) , včetně typu použitého ověřování a zabezpečení používaného pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="596f1-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="596f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="596f1-104">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="596f1-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="596f1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="596f1-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="596f1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="596f1-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="596f1-107">Attributes</span></span>  
  
|<span data-ttu-id="596f1-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="596f1-108">Attribute</span></span>|<span data-ttu-id="596f1-109">Popis</span><span class="sxs-lookup"><span data-stu-id="596f1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="596f1-110">režim</span><span class="sxs-lookup"><span data-stu-id="596f1-110">mode</span></span>|<span data-ttu-id="596f1-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="596f1-111">Optional.</span></span> <span data-ttu-id="596f1-112">Určuje typ zabezpečení, který používají partneři nakonfigurované s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="596f1-112">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="596f1-113">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="596f1-113">The default value is `Message`.</span></span> <span data-ttu-id="596f1-114">Tento atribut je typu <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="596f1-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="596f1-115">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="596f1-115">mode Attribute</span></span>  
  
|<span data-ttu-id="596f1-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="596f1-116">Value</span></span>|<span data-ttu-id="596f1-117">Description</span><span class="sxs-lookup"><span data-stu-id="596f1-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="596f1-118">Zpráva</span><span class="sxs-lookup"><span data-stu-id="596f1-118">Message</span></span>|<span data-ttu-id="596f1-119">Zabezpečení SOAP zajišťuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="596f1-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="596f1-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="596f1-120">None</span></span>|<span data-ttu-id="596f1-121">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="596f1-121">Security is disabled.</span></span>|  
|<span data-ttu-id="596f1-122">Přenos</span><span class="sxs-lookup"><span data-stu-id="596f1-122">Transport</span></span>|<span data-ttu-id="596f1-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="596f1-123">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="596f1-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="596f1-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="596f1-125">Protokol HTTPS zajišťuje ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="596f1-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="596f1-126">Zprávy SOAP poskytují bohatě typy přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="596f1-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="596f1-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="596f1-127">Child Elements</span></span>  
  
|<span data-ttu-id="596f1-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="596f1-128">Element</span></span>|<span data-ttu-id="596f1-129">Description</span><span class="sxs-lookup"><span data-stu-id="596f1-129">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="596f1-130">Definuje typ přenosu pro zabezpečené zprávy odesílané partnerskými uzly nakonfigurovanými pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="596f1-130">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="596f1-131">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="596f1-131">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="596f1-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="596f1-132">Parent Elements</span></span>  
  
|<span data-ttu-id="596f1-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="596f1-133">Element</span></span>|<span data-ttu-id="596f1-134">Description</span><span class="sxs-lookup"><span data-stu-id="596f1-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="596f1-135">Definuje všechny schopnosti vazby pro [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="596f1-135">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="596f1-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="596f1-136">Remarks</span></span>  
 <span data-ttu-id="596f1-137">Zabezpečení může být specifické pro zprávy nebo pro přenos.</span><span class="sxs-lookup"><span data-stu-id="596f1-137">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="596f1-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="596f1-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="596f1-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="596f1-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="596f1-140">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="596f1-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="596f1-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="596f1-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="596f1-142">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="596f1-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="596f1-143">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="596f1-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
