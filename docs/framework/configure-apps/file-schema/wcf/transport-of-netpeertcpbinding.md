---
title: '&lt;transport&gt; – &lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: b929c97d0b5d9e021a71e4b88dd3d8a5f2f909a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677001"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="23228-102">&lt;transport&gt; – &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="23228-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="23228-103">Určuje nastavení zabezpečení na úrovni přenosu při použití [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="23228-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="23228-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="23228-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="23228-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="23228-105">\<bindings></span></span>  
<span data-ttu-id="23228-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="23228-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="23228-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="23228-107">\<binding></span></span>  
<span data-ttu-id="23228-108">\<security></span><span class="sxs-lookup"><span data-stu-id="23228-108">\<security></span></span>  
<span data-ttu-id="23228-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="23228-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23228-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23228-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23228-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="23228-111">Attributes and Elements</span></span>  
 <span data-ttu-id="23228-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="23228-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23228-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="23228-113">Attributes</span></span>  
  
|<span data-ttu-id="23228-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="23228-114">Attribute</span></span>|<span data-ttu-id="23228-115">Popis</span><span class="sxs-lookup"><span data-stu-id="23228-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23228-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="23228-116">credentialType</span></span>|<span data-ttu-id="23228-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="23228-117">Optional.</span></span> <span data-ttu-id="23228-118">Určuje typ pověření použitá k ověření zprávy odeslané s rovnocenný přenos.</span><span class="sxs-lookup"><span data-stu-id="23228-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="23228-119">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="23228-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="23228-120">credentialType atribut</span><span class="sxs-lookup"><span data-stu-id="23228-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="23228-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="23228-121">Value</span></span>|<span data-ttu-id="23228-122">Popis</span><span class="sxs-lookup"><span data-stu-id="23228-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="23228-123">Certifikát</span><span class="sxs-lookup"><span data-stu-id="23228-123">Certificate</span></span>|<span data-ttu-id="23228-124">Ověřování rovnocenný kanál přenos vyžaduje x X509 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="23228-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="23228-125">Heslo</span><span class="sxs-lookup"><span data-stu-id="23228-125">Password</span></span>|<span data-ttu-id="23228-126">Ověřování rovnocenný kanál přenos vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="23228-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23228-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="23228-127">Child Elements</span></span>  
 <span data-ttu-id="23228-128">Žádná</span><span class="sxs-lookup"><span data-stu-id="23228-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23228-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="23228-129">Parent Elements</span></span>  
  
|<span data-ttu-id="23228-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="23228-130">Element</span></span>|<span data-ttu-id="23228-131">Popis</span><span class="sxs-lookup"><span data-stu-id="23228-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23228-132">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="23228-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="23228-133">Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="23228-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23228-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23228-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="23228-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="23228-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="23228-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="23228-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="23228-137">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="23228-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="23228-138">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="23228-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="23228-139">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="23228-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
