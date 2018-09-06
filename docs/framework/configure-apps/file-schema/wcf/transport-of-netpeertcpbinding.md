---
title: '&lt;transport&gt; – &lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 2b89ae090d24ff6aad1aae1b39a0a18961bd2537
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43869776"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="bee74-102">&lt;transport&gt; – &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="bee74-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="bee74-103">Určuje nastavení zabezpečení na úrovni přenosu při použití [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bee74-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="bee74-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bee74-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bee74-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="bee74-105">\<bindings></span></span>  
<span data-ttu-id="bee74-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="bee74-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="bee74-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="bee74-107">\<binding></span></span>  
<span data-ttu-id="bee74-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="bee74-108">\<security></span></span>  
<span data-ttu-id="bee74-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="bee74-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bee74-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bee74-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bee74-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bee74-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bee74-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bee74-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bee74-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="bee74-113">Attributes</span></span>  
  
|<span data-ttu-id="bee74-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="bee74-114">Attribute</span></span>|<span data-ttu-id="bee74-115">Popis</span><span class="sxs-lookup"><span data-stu-id="bee74-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bee74-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="bee74-116">credentialType</span></span>|<span data-ttu-id="bee74-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="bee74-117">Optional.</span></span> <span data-ttu-id="bee74-118">Určuje typ pověření použitá k ověření zprávy odeslané s rovnocenný přenos.</span><span class="sxs-lookup"><span data-stu-id="bee74-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="bee74-119">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="bee74-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="bee74-120">credentialType atribut</span><span class="sxs-lookup"><span data-stu-id="bee74-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="bee74-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bee74-121">Value</span></span>|<span data-ttu-id="bee74-122">Popis</span><span class="sxs-lookup"><span data-stu-id="bee74-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bee74-123">Certifikát</span><span class="sxs-lookup"><span data-stu-id="bee74-123">Certificate</span></span>|<span data-ttu-id="bee74-124">Ověřování rovnocenný kanál přenos vyžaduje x X509 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="bee74-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="bee74-125">Heslo</span><span class="sxs-lookup"><span data-stu-id="bee74-125">Password</span></span>|<span data-ttu-id="bee74-126">Ověřování rovnocenný kanál přenos vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="bee74-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bee74-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bee74-127">Child Elements</span></span>  
 <span data-ttu-id="bee74-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="bee74-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bee74-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bee74-129">Parent Elements</span></span>  
  
|<span data-ttu-id="bee74-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="bee74-130">Element</span></span>|<span data-ttu-id="bee74-131">Popis</span><span class="sxs-lookup"><span data-stu-id="bee74-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bee74-132">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="bee74-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="bee74-133">Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="bee74-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bee74-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="bee74-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="bee74-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bee74-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="bee74-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="bee74-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bee74-137">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="bee74-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="bee74-138">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="bee74-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="bee74-139">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="bee74-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
