---
title: "&lt;security&gt; – &lt;peerTransport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d08d839d0eb80c23b96f87cf26d3d68db7d358f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="6d444-102">&lt;security&gt; – &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="6d444-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="6d444-103">Obsahuje nastavení zabezpečení, které jsou přidružené k rovnocenného kanálu, včetně typu ověřování použité a zabezpečení použít pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="6d444-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="6d444-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6d444-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6d444-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="6d444-105">\<bindings></span></span>  
<span data-ttu-id="6d444-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6d444-106">\<customBinding></span></span>  
<span data-ttu-id="6d444-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="6d444-107">\<binding></span></span>  
<span data-ttu-id="6d444-108">\<– peerTransport ></span><span class="sxs-lookup"><span data-stu-id="6d444-108">\<peerTransport></span></span>  
<span data-ttu-id="6d444-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="6d444-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d444-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d444-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">  
    <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
</security  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d444-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d444-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6d444-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6d444-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d444-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d444-113">Attributes</span></span>  
  
|<span data-ttu-id="6d444-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="6d444-114">Attribute</span></span>|<span data-ttu-id="6d444-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6d444-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="6d444-116">Určuje typ zabezpečení, které se má použít.</span><span class="sxs-lookup"><span data-stu-id="6d444-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="6d444-117">Výchozí hodnota je zpráva.</span><span class="sxs-lookup"><span data-stu-id="6d444-117">The default value is Message.</span></span> <span data-ttu-id="6d444-118">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6d444-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6d444-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="6d444-119">mode Attribute</span></span>  
  
|<span data-ttu-id="6d444-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6d444-120">Value</span></span>|<span data-ttu-id="6d444-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6d444-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="6d444-122">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="6d444-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="6d444-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6d444-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="6d444-124">Zabezpečení protokolu SOAP poskytuje ověřování, integrity a důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="6d444-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="6d444-125">HTTPS poskytuje možnosti ověřování a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="6d444-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="6d444-126">Protokolu SOAP zprávy poskytují typy bohaté přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="6d444-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d444-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d444-127">Child Elements</span></span>  
  
|<span data-ttu-id="6d444-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d444-128">Element</span></span>|<span data-ttu-id="6d444-129">Popis</span><span class="sxs-lookup"><span data-stu-id="6d444-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d444-130">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="6d444-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="6d444-131">Definuje sdílené přenos vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="6d444-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="6d444-132">Tento element má `clientCredentialType` atribut, který určuje pověření, která má být použit při interakci s služby.</span><span class="sxs-lookup"><span data-stu-id="6d444-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="6d444-133">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="6d444-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="6d444-134">Tento element je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="6d444-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d444-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6d444-135">Parent Elements</span></span>  
  
|<span data-ttu-id="6d444-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="6d444-136">Element</span></span>|<span data-ttu-id="6d444-137">Popis</span><span class="sxs-lookup"><span data-stu-id="6d444-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d444-138">\<– peerTransport ></span><span class="sxs-lookup"><span data-stu-id="6d444-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="6d444-139">Definuje sdílené přenos vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="6d444-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d444-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d444-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="6d444-141">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="6d444-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="6d444-142">Přenosy</span><span class="sxs-lookup"><span data-stu-id="6d444-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="6d444-143">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="6d444-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="6d444-144">Vazby</span><span class="sxs-lookup"><span data-stu-id="6d444-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6d444-145">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="6d444-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="6d444-146">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="6d444-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="6d444-147">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6d444-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
