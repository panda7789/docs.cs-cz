---
title: "&lt;transport&gt; – &lt;peerTransport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 69b62699f5db0ab11fac3cc4d1ba4e2aa022934d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="2d385-102">&lt;transport&gt; – &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="2d385-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="2d385-103">Určuje typ přenosu pro zabezpečené zprávy odeslané partnerské uzly, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="2d385-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="2d385-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2d385-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2d385-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="2d385-105">\<bindings></span></span>  
<span data-ttu-id="2d385-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2d385-106">\<customBinding></span></span>  
<span data-ttu-id="2d385-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="2d385-107">\<binding></span></span>  
<span data-ttu-id="2d385-108">\<– peerTransport ></span><span class="sxs-lookup"><span data-stu-id="2d385-108">\<peerTransport></span></span>  
<span data-ttu-id="2d385-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="2d385-109">\<security></span></span>  
<span data-ttu-id="2d385-110">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="2d385-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d385-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d385-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d385-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2d385-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2d385-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2d385-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d385-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="2d385-114">Attributes</span></span>  
  
|<span data-ttu-id="2d385-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="2d385-115">Attribute</span></span>|<span data-ttu-id="2d385-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2d385-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2d385-117">CredentialType</span><span class="sxs-lookup"><span data-stu-id="2d385-117">credentialType</span></span>|<span data-ttu-id="2d385-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2d385-118">Optional.</span></span> <span data-ttu-id="2d385-119">Určuje typ přihlašovacích údajů, které používají k ověření zprávy odeslané s sdílené přenosu.</span><span class="sxs-lookup"><span data-stu-id="2d385-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="2d385-120">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2d385-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="2d385-121">credentialType atribut</span><span class="sxs-lookup"><span data-stu-id="2d385-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="2d385-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2d385-122">Value</span></span>|<span data-ttu-id="2d385-123">Popis</span><span class="sxs-lookup"><span data-stu-id="2d385-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2d385-124">certifikát</span><span class="sxs-lookup"><span data-stu-id="2d385-124">Certificate</span></span>|<span data-ttu-id="2d385-125">Ověřování přenosu kanál sdílené vyžaduje X509 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="2d385-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="2d385-126">Heslo</span><span class="sxs-lookup"><span data-stu-id="2d385-126">Password</span></span>|<span data-ttu-id="2d385-127">Ověřování přenosu kanál sdílené vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="2d385-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d385-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2d385-128">Child Elements</span></span>  
 <span data-ttu-id="2d385-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="2d385-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d385-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2d385-130">Parent Elements</span></span>  
  
|<span data-ttu-id="2d385-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="2d385-131">Element</span></span>|<span data-ttu-id="2d385-132">Popis</span><span class="sxs-lookup"><span data-stu-id="2d385-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d385-133">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="2d385-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="2d385-134">Definuje nastavení zabezpečení pro sdílené přenosu.</span><span class="sxs-lookup"><span data-stu-id="2d385-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d385-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d385-135">Remarks</span></span>  
 <span data-ttu-id="2d385-136">Tento element je nastavena, jen pokud atribut režimu [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) je nastaven na `Transport` nebo `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="2d385-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d385-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d385-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="2d385-138">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="2d385-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="2d385-139">Přenosy</span><span class="sxs-lookup"><span data-stu-id="2d385-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="2d385-140">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="2d385-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="2d385-141">Vazby</span><span class="sxs-lookup"><span data-stu-id="2d385-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2d385-142">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="2d385-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2d385-143">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="2d385-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2d385-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2d385-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
