---
title: "&lt;transport&gt; – &lt;netPeerTcpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6cc5e0b2aa52c8fa37e6148f66dc24fca273a640
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="b874f-102">&lt;transport&gt; – &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="b874f-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="b874f-103">Určuje nastavení pro zabezpečení na úrovni přenosu při použití [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b874f-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="b874f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b874f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b874f-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b874f-105">\<bindings></span></span>  
<span data-ttu-id="b874f-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="b874f-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="b874f-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="b874f-107">\<binding></span></span>  
<span data-ttu-id="b874f-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="b874f-108">\<security></span></span>  
<span data-ttu-id="b874f-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="b874f-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b874f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b874f-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b874f-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b874f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b874f-112">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b874f-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b874f-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="b874f-113">Attributes</span></span>  
  
|<span data-ttu-id="b874f-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="b874f-114">Attribute</span></span>|<span data-ttu-id="b874f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b874f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b874f-116">CredentialType</span><span class="sxs-lookup"><span data-stu-id="b874f-116">credentialType</span></span>|<span data-ttu-id="b874f-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="b874f-117">Optional.</span></span> <span data-ttu-id="b874f-118">Určuje typ přihlašovacích údajů, které používají k ověření zprávy odeslané s sdílené přenosu.</span><span class="sxs-lookup"><span data-stu-id="b874f-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="b874f-119">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="b874f-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="b874f-120">credentialType atribut</span><span class="sxs-lookup"><span data-stu-id="b874f-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="b874f-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b874f-121">Value</span></span>|<span data-ttu-id="b874f-122">Popis</span><span class="sxs-lookup"><span data-stu-id="b874f-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b874f-123">certifikát</span><span class="sxs-lookup"><span data-stu-id="b874f-123">Certificate</span></span>|<span data-ttu-id="b874f-124">Ověřování přenosu kanál sdílené vyžaduje X509 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="b874f-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="b874f-125">Heslo</span><span class="sxs-lookup"><span data-stu-id="b874f-125">Password</span></span>|<span data-ttu-id="b874f-126">Ověřování přenosu kanál sdílené vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="b874f-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b874f-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b874f-127">Child Elements</span></span>  
 <span data-ttu-id="b874f-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="b874f-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b874f-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b874f-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b874f-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="b874f-130">Element</span></span>|<span data-ttu-id="b874f-131">Popis</span><span class="sxs-lookup"><span data-stu-id="b874f-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b874f-132">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="b874f-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="b874f-133">Definuje nastavení zabezpečení pro [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b874f-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b874f-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b874f-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="b874f-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b874f-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b874f-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="b874f-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b874f-137">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b874f-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b874f-138">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="b874f-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b874f-139">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="b874f-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
