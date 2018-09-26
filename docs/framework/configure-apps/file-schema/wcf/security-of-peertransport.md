---
title: '&lt;security&gt; – &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
author: BrucePerlerMS
ms.openlocfilehash: 152087550d3fa881a7a88271d9c91dfcc5c894c8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176757"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="291d0-102">&lt;security&gt; – &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="291d0-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="291d0-103">Obsahuje nastavení zabezpečení související s rovnocenným kanálem, zahrnující typ použitého ověřování a zabezpečení pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="291d0-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="291d0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="291d0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="291d0-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="291d0-105">\<bindings></span></span>  
<span data-ttu-id="291d0-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="291d0-106">\<customBinding></span></span>  
<span data-ttu-id="291d0-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="291d0-107">\<binding></span></span>  
<span data-ttu-id="291d0-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="291d0-108">\<peerTransport></span></span>  
<span data-ttu-id="291d0-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="291d0-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="291d0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="291d0-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">  
    <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
</security  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="291d0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="291d0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="291d0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="291d0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="291d0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="291d0-113">Attributes</span></span>  
  
|<span data-ttu-id="291d0-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="291d0-114">Attribute</span></span>|<span data-ttu-id="291d0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="291d0-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="291d0-116">Určuje typ zabezpečení má být použita.</span><span class="sxs-lookup"><span data-stu-id="291d0-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="291d0-117">Výchozí hodnota je zpráva.</span><span class="sxs-lookup"><span data-stu-id="291d0-117">The default value is Message.</span></span> <span data-ttu-id="291d0-118">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="291d0-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="291d0-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="291d0-119">mode Attribute</span></span>  
  
|<span data-ttu-id="291d0-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="291d0-120">Value</span></span>|<span data-ttu-id="291d0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="291d0-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="291d0-122">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="291d0-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="291d0-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="291d0-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="291d0-124">Zabezpečení protokolu SOAP poskytuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="291d0-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="291d0-125">HTTPS zajišťuje ověřování a zachováním důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="291d0-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="291d0-126">Zprávy protokolu SOAP poskytuje typy bohaté přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="291d0-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="291d0-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="291d0-127">Child Elements</span></span>  
  
|<span data-ttu-id="291d0-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="291d0-128">Element</span></span>|<span data-ttu-id="291d0-129">Popis</span><span class="sxs-lookup"><span data-stu-id="291d0-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="291d0-130">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="291d0-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="291d0-131">Definuje rovnocenný přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="291d0-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="291d0-132">Tento element nemá `clientCredentialType` atribut, který určuje přihlašovací údaje, které se použije při komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="291d0-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="291d0-133">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="291d0-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="291d0-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="291d0-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="291d0-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="291d0-135">Parent Elements</span></span>  
  
|<span data-ttu-id="291d0-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="291d0-136">Element</span></span>|<span data-ttu-id="291d0-137">Popis</span><span class="sxs-lookup"><span data-stu-id="291d0-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="291d0-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="291d0-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="291d0-139">Definuje rovnocenný přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="291d0-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="291d0-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="291d0-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="291d0-141">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="291d0-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="291d0-142">Přenosy</span><span class="sxs-lookup"><span data-stu-id="291d0-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="291d0-143">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="291d0-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="291d0-144">Vazby</span><span class="sxs-lookup"><span data-stu-id="291d0-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="291d0-145">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="291d0-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="291d0-146">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="291d0-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="291d0-147">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="291d0-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
