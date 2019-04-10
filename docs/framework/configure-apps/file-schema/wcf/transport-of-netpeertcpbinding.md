---
title: <transport> of <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 157637615abafbd5913e4d90b702bb0224d5f121
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204871"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="7b3f2-102">\<přenos > z \<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="7b3f2-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="7b3f2-103">Určuje nastavení zabezpečení na úrovni přenosu při použití [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7b3f2-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="7b3f2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b3f2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b3f2-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7b3f2-105">\<bindings></span></span>  
<span data-ttu-id="7b3f2-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="7b3f2-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="7b3f2-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="7b3f2-107">\<binding></span></span>  
<span data-ttu-id="7b3f2-108">\<security></span><span class="sxs-lookup"><span data-stu-id="7b3f2-108">\<security></span></span>  
<span data-ttu-id="7b3f2-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="7b3f2-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b3f2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b3f2-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b3f2-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7b3f2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7b3f2-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b3f2-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b3f2-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b3f2-113">Attributes</span></span>  
  
|<span data-ttu-id="7b3f2-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b3f2-114">Attribute</span></span>|<span data-ttu-id="7b3f2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="7b3f2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b3f2-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="7b3f2-116">credentialType</span></span>|<span data-ttu-id="7b3f2-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7b3f2-117">Optional.</span></span> <span data-ttu-id="7b3f2-118">Určuje typ pověření použitá k ověření zprávy odeslané s rovnocenný přenos.</span><span class="sxs-lookup"><span data-stu-id="7b3f2-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="7b3f2-119">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="7b3f2-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="7b3f2-120">credentialType atribut</span><span class="sxs-lookup"><span data-stu-id="7b3f2-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="7b3f2-121">Value</span><span class="sxs-lookup"><span data-stu-id="7b3f2-121">Value</span></span>|<span data-ttu-id="7b3f2-122">Popis</span><span class="sxs-lookup"><span data-stu-id="7b3f2-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7b3f2-123">Certifikát</span><span class="sxs-lookup"><span data-stu-id="7b3f2-123">Certificate</span></span>|<span data-ttu-id="7b3f2-124">Ověřování rovnocenný kanál přenos vyžaduje x X509 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="7b3f2-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="7b3f2-125">Heslo</span><span class="sxs-lookup"><span data-stu-id="7b3f2-125">Password</span></span>|<span data-ttu-id="7b3f2-126">Ověřování rovnocenný kanál přenos vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="7b3f2-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b3f2-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7b3f2-127">Child Elements</span></span>  
 <span data-ttu-id="7b3f2-128">Žádný</span><span class="sxs-lookup"><span data-stu-id="7b3f2-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b3f2-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b3f2-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7b3f2-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b3f2-130">Element</span></span>|<span data-ttu-id="7b3f2-131">Popis</span><span class="sxs-lookup"><span data-stu-id="7b3f2-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b3f2-132">\<security></span><span class="sxs-lookup"><span data-stu-id="7b3f2-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="7b3f2-133">Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="7b3f2-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b3f2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b3f2-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="7b3f2-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7b3f2-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7b3f2-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="7b3f2-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7b3f2-137">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="7b3f2-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7b3f2-138">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7b3f2-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7b3f2-139">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="7b3f2-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
