---
title: <transport> z <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 837d01540fa63579877ab4085bd8034c78f2fbe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915563"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="648c6-102">\<> přenosu > \<NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="648c6-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="648c6-103">Určuje nastavení zabezpečení na úrovni přenosu při použití [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="648c6-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="648c6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="648c6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="648c6-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="648c6-105">\<bindings></span></span>  
<span data-ttu-id="648c6-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="648c6-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="648c6-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="648c6-107">\<binding></span></span>  
<span data-ttu-id="648c6-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="648c6-108">\<security></span></span>  
<span data-ttu-id="648c6-109">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="648c6-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="648c6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="648c6-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="648c6-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="648c6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="648c6-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="648c6-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="648c6-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="648c6-113">Attributes</span></span>  
  
|<span data-ttu-id="648c6-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="648c6-114">Attribute</span></span>|<span data-ttu-id="648c6-115">Popis</span><span class="sxs-lookup"><span data-stu-id="648c6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="648c6-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="648c6-116">credentialType</span></span>|<span data-ttu-id="648c6-117">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="648c6-117">Optional.</span></span> <span data-ttu-id="648c6-118">Určuje typ přihlašovacích údajů, které se používají k ověření zpráv odesílaných pomocí partnerského přenosu.</span><span class="sxs-lookup"><span data-stu-id="648c6-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="648c6-119">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="648c6-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="648c6-120">credentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="648c6-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="648c6-121">Value</span><span class="sxs-lookup"><span data-stu-id="648c6-121">Value</span></span>|<span data-ttu-id="648c6-122">Popis</span><span class="sxs-lookup"><span data-stu-id="648c6-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="648c6-123">Certifikát</span><span class="sxs-lookup"><span data-stu-id="648c6-123">Certificate</span></span>|<span data-ttu-id="648c6-124">Ověřování přenosu rovnocenného kanálu vyžaduje certifikát x509.</span><span class="sxs-lookup"><span data-stu-id="648c6-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="648c6-125">Heslo</span><span class="sxs-lookup"><span data-stu-id="648c6-125">Password</span></span>|<span data-ttu-id="648c6-126">Ověření přenosu rovnocenného kanálu vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="648c6-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="648c6-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="648c6-127">Child Elements</span></span>  
 <span data-ttu-id="648c6-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="648c6-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="648c6-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="648c6-129">Parent Elements</span></span>  
  
|<span data-ttu-id="648c6-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="648c6-130">Element</span></span>|<span data-ttu-id="648c6-131">Popis</span><span class="sxs-lookup"><span data-stu-id="648c6-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="648c6-132">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="648c6-132">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="648c6-133">Definuje nastavení zabezpečení pro [ \<NetPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="648c6-133">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="648c6-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="648c6-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="648c6-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="648c6-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="648c6-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="648c6-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="648c6-137">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="648c6-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="648c6-138">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="648c6-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="648c6-139">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="648c6-139">\<binding></span></span>](../../../misc/binding.md)
