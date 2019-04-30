---
title: <transport> z <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 157637615abafbd5913e4d90b702bb0224d5f121
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788320"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="d331e-102">\<přenos > z \<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="d331e-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="d331e-103">Určuje nastavení zabezpečení na úrovni přenosu při použití [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d331e-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="d331e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d331e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d331e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d331e-105">\<bindings></span></span>  
<span data-ttu-id="d331e-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="d331e-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="d331e-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d331e-107">\<binding></span></span>  
<span data-ttu-id="d331e-108">\<security></span><span class="sxs-lookup"><span data-stu-id="d331e-108">\<security></span></span>  
<span data-ttu-id="d331e-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="d331e-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d331e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d331e-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d331e-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d331e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d331e-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d331e-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d331e-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d331e-113">Attributes</span></span>  
  
|<span data-ttu-id="d331e-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d331e-114">Attribute</span></span>|<span data-ttu-id="d331e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d331e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d331e-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="d331e-116">credentialType</span></span>|<span data-ttu-id="d331e-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d331e-117">Optional.</span></span> <span data-ttu-id="d331e-118">Určuje typ pověření použitá k ověření zprávy odeslané s rovnocenný přenos.</span><span class="sxs-lookup"><span data-stu-id="d331e-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="d331e-119">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d331e-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="d331e-120">credentialType atribut</span><span class="sxs-lookup"><span data-stu-id="d331e-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="d331e-121">Value</span><span class="sxs-lookup"><span data-stu-id="d331e-121">Value</span></span>|<span data-ttu-id="d331e-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d331e-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d331e-123">Certifikát</span><span class="sxs-lookup"><span data-stu-id="d331e-123">Certificate</span></span>|<span data-ttu-id="d331e-124">Ověřování rovnocenný kanál přenos vyžaduje x X509 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d331e-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="d331e-125">Heslo</span><span class="sxs-lookup"><span data-stu-id="d331e-125">Password</span></span>|<span data-ttu-id="d331e-126">Ověřování rovnocenný kanál přenos vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="d331e-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d331e-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d331e-127">Child Elements</span></span>  
 <span data-ttu-id="d331e-128">Žádný</span><span class="sxs-lookup"><span data-stu-id="d331e-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d331e-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d331e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d331e-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="d331e-130">Element</span></span>|<span data-ttu-id="d331e-131">Popis</span><span class="sxs-lookup"><span data-stu-id="d331e-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d331e-132">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="d331e-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="d331e-133">Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d331e-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d331e-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d331e-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="d331e-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d331e-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d331e-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="d331e-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d331e-137">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="d331e-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d331e-138">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d331e-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d331e-139">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d331e-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
