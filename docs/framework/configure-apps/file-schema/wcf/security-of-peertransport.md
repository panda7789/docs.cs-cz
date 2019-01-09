---
title: '&lt;security&gt; – &lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 901a1d0b29fa6ea7d9e520b379dc7c7ff1d1e522
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151953"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="76ddf-102">&lt;security&gt; – &lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="76ddf-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="76ddf-103">Obsahuje nastavení zabezpečení související s rovnocenným kanálem, zahrnující typ použitého ověřování a zabezpečení pro přenos zpráv.</span><span class="sxs-lookup"><span data-stu-id="76ddf-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="76ddf-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="76ddf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="76ddf-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="76ddf-105">\<bindings></span></span>  
<span data-ttu-id="76ddf-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="76ddf-106">\<customBinding></span></span>  
<span data-ttu-id="76ddf-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="76ddf-107">\<binding></span></span>  
<span data-ttu-id="76ddf-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="76ddf-108">\<peerTransport></span></span>  
<span data-ttu-id="76ddf-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="76ddf-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ddf-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76ddf-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76ddf-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76ddf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="76ddf-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76ddf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76ddf-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="76ddf-113">Attributes</span></span>  
  
|<span data-ttu-id="76ddf-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="76ddf-114">Attribute</span></span>|<span data-ttu-id="76ddf-115">Popis</span><span class="sxs-lookup"><span data-stu-id="76ddf-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="76ddf-116">Určuje typ zabezpečení má být použita.</span><span class="sxs-lookup"><span data-stu-id="76ddf-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="76ddf-117">Výchozí hodnota je zpráva.</span><span class="sxs-lookup"><span data-stu-id="76ddf-117">The default value is Message.</span></span> <span data-ttu-id="76ddf-118">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="76ddf-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="76ddf-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="76ddf-119">mode Attribute</span></span>  
  
|<span data-ttu-id="76ddf-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="76ddf-120">Value</span></span>|<span data-ttu-id="76ddf-121">Popis</span><span class="sxs-lookup"><span data-stu-id="76ddf-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="76ddf-122">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="76ddf-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="76ddf-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="76ddf-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="76ddf-124">Zabezpečení protokolu SOAP poskytuje ověřování, integritu a důvěrnost.</span><span class="sxs-lookup"><span data-stu-id="76ddf-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="76ddf-125">HTTPS zajišťuje ověřování a zachováním důvěrnosti.</span><span class="sxs-lookup"><span data-stu-id="76ddf-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="76ddf-126">Zprávy protokolu SOAP poskytuje typy bohaté přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="76ddf-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76ddf-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76ddf-127">Child Elements</span></span>  
  
|<span data-ttu-id="76ddf-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="76ddf-128">Element</span></span>|<span data-ttu-id="76ddf-129">Popis</span><span class="sxs-lookup"><span data-stu-id="76ddf-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76ddf-130">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="76ddf-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="76ddf-131">Definuje rovnocenný přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="76ddf-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="76ddf-132">Tento element nemá `clientCredentialType` atribut, který určuje přihlašovací údaje, které se použije při komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="76ddf-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="76ddf-133">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="76ddf-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="76ddf-134">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="76ddf-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76ddf-135">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76ddf-135">Parent Elements</span></span>  
  
|<span data-ttu-id="76ddf-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="76ddf-136">Element</span></span>|<span data-ttu-id="76ddf-137">Popis</span><span class="sxs-lookup"><span data-stu-id="76ddf-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76ddf-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="76ddf-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="76ddf-139">Definuje rovnocenný přenos pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="76ddf-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76ddf-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="76ddf-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="76ddf-141">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="76ddf-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="76ddf-142">Přenosy</span><span class="sxs-lookup"><span data-stu-id="76ddf-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="76ddf-143">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="76ddf-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="76ddf-144">Vazby</span><span class="sxs-lookup"><span data-stu-id="76ddf-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="76ddf-145">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="76ddf-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="76ddf-146">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="76ddf-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="76ddf-147">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="76ddf-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
