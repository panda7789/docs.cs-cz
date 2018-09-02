---
title: '&lt;transport&gt; – &lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 2b89ae090d24ff6aad1aae1b39a0a18961bd2537
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405661"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="de2ab-102">&lt;transport&gt; – &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="de2ab-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="de2ab-103">Určuje nastavení zabezpečení na úrovni přenosu při použití [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="de2ab-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="de2ab-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de2ab-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="de2ab-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="de2ab-105">\<bindings></span></span>  
<span data-ttu-id="de2ab-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="de2ab-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="de2ab-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="de2ab-107">\<binding></span></span>  
<span data-ttu-id="de2ab-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="de2ab-108">\<security></span></span>  
<span data-ttu-id="de2ab-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="de2ab-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de2ab-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de2ab-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de2ab-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="de2ab-111">Attributes and Elements</span></span>  
 <span data-ttu-id="de2ab-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="de2ab-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de2ab-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="de2ab-113">Attributes</span></span>  
  
|<span data-ttu-id="de2ab-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="de2ab-114">Attribute</span></span>|<span data-ttu-id="de2ab-115">Popis</span><span class="sxs-lookup"><span data-stu-id="de2ab-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de2ab-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="de2ab-116">credentialType</span></span>|<span data-ttu-id="de2ab-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="de2ab-117">Optional.</span></span> <span data-ttu-id="de2ab-118">Určuje typ pověření použitá k ověření zprávy odeslané s rovnocenný přenos.</span><span class="sxs-lookup"><span data-stu-id="de2ab-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="de2ab-119">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="de2ab-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="de2ab-120">credentialType atribut</span><span class="sxs-lookup"><span data-stu-id="de2ab-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="de2ab-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="de2ab-121">Value</span></span>|<span data-ttu-id="de2ab-122">Popis</span><span class="sxs-lookup"><span data-stu-id="de2ab-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="de2ab-123">Certifikát</span><span class="sxs-lookup"><span data-stu-id="de2ab-123">Certificate</span></span>|<span data-ttu-id="de2ab-124">Ověřování rovnocenný kanál přenos vyžaduje x X509 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="de2ab-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="de2ab-125">Heslo</span><span class="sxs-lookup"><span data-stu-id="de2ab-125">Password</span></span>|<span data-ttu-id="de2ab-126">Ověřování rovnocenný kanál přenos vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="de2ab-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de2ab-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="de2ab-127">Child Elements</span></span>  
 <span data-ttu-id="de2ab-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="de2ab-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de2ab-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="de2ab-129">Parent Elements</span></span>  
  
|<span data-ttu-id="de2ab-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="de2ab-130">Element</span></span>|<span data-ttu-id="de2ab-131">Popis</span><span class="sxs-lookup"><span data-stu-id="de2ab-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de2ab-132">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="de2ab-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="de2ab-133">Definuje nastavení zabezpečení [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="de2ab-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de2ab-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="de2ab-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="de2ab-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="de2ab-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="de2ab-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="de2ab-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="de2ab-137">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="de2ab-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="de2ab-138">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="de2ab-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="de2ab-139">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="de2ab-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
