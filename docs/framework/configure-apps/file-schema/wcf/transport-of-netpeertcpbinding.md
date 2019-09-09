---
title: <transport> z <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 08be5d752f8422ebe6442b295195f21b16a274c0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399319"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="f2a76-102">\<> přenosu > \<NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="f2a76-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="f2a76-103">Určuje nastavení zabezpečení na úrovni přenosu při použití [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f2a76-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
<span data-ttu-id="f2a76-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2a76-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f2a76-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f2a76-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f2a76-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f2a76-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f2a76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f2a76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="f2a76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="f2a76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f2a76-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-netpeerbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f2a76-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)</span></span>\
<span data-ttu-id="f2a76-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> přenosu**</span><span class="sxs-lookup"><span data-stu-id="f2a76-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a76-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2a76-111">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2a76-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f2a76-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f2a76-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f2a76-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2a76-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f2a76-114">Attributes</span></span>  
  
|<span data-ttu-id="f2a76-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="f2a76-115">Attribute</span></span>|<span data-ttu-id="f2a76-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f2a76-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2a76-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="f2a76-117">credentialType</span></span>|<span data-ttu-id="f2a76-118">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="f2a76-118">Optional.</span></span> <span data-ttu-id="f2a76-119">Určuje typ přihlašovacích údajů, které se používají k ověření zpráv odesílaných pomocí partnerského přenosu.</span><span class="sxs-lookup"><span data-stu-id="f2a76-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="f2a76-120">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="f2a76-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="f2a76-121">credentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="f2a76-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="f2a76-122">Value</span><span class="sxs-lookup"><span data-stu-id="f2a76-122">Value</span></span>|<span data-ttu-id="f2a76-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f2a76-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f2a76-124">Certifikát</span><span class="sxs-lookup"><span data-stu-id="f2a76-124">Certificate</span></span>|<span data-ttu-id="f2a76-125">Ověřování přenosu rovnocenného kanálu vyžaduje certifikát x509.</span><span class="sxs-lookup"><span data-stu-id="f2a76-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="f2a76-126">Heslo</span><span class="sxs-lookup"><span data-stu-id="f2a76-126">Password</span></span>|<span data-ttu-id="f2a76-127">Ověření přenosu rovnocenného kanálu vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="f2a76-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2a76-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f2a76-128">Child Elements</span></span>  
 <span data-ttu-id="f2a76-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="f2a76-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2a76-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f2a76-130">Parent Elements</span></span>  
  
|<span data-ttu-id="f2a76-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="f2a76-131">Element</span></span>|<span data-ttu-id="f2a76-132">Popis</span><span class="sxs-lookup"><span data-stu-id="f2a76-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2a76-133">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f2a76-133">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="f2a76-134">Definuje nastavení zabezpečení pro [ \<NetPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f2a76-134">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2a76-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2a76-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="f2a76-136">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f2a76-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f2a76-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="f2a76-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f2a76-138">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="f2a76-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f2a76-139">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f2a76-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f2a76-140">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="f2a76-140">\<binding></span></span>](../../../misc/binding.md)
