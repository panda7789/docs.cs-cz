---
title: <transport> z <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 49b31a889d192d190125214e89ba09305114eb7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735971"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="042ec-102">\<transport> z \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="042ec-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="042ec-103">Určuje nastavení zabezpečení na úrovni přenosu při použití [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="042ec-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="042ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="042ec-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="042ec-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="042ec-105">Attributes and Elements</span></span>  
 <span data-ttu-id="042ec-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="042ec-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="042ec-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="042ec-107">Attributes</span></span>  
  
|<span data-ttu-id="042ec-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="042ec-108">Attribute</span></span>|<span data-ttu-id="042ec-109">Popis</span><span class="sxs-lookup"><span data-stu-id="042ec-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="042ec-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="042ec-110">credentialType</span></span>|<span data-ttu-id="042ec-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="042ec-111">Optional.</span></span> <span data-ttu-id="042ec-112">Určuje typ přihlašovacích údajů, které se používají k ověření zpráv odesílaných pomocí partnerského přenosu.</span><span class="sxs-lookup"><span data-stu-id="042ec-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="042ec-113">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="042ec-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="042ec-114">credentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="042ec-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="042ec-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="042ec-115">Value</span></span>|<span data-ttu-id="042ec-116">Description</span><span class="sxs-lookup"><span data-stu-id="042ec-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="042ec-117">Certifikát</span><span class="sxs-lookup"><span data-stu-id="042ec-117">Certificate</span></span>|<span data-ttu-id="042ec-118">Ověřování přenosu rovnocenného kanálu vyžaduje certifikát x509.</span><span class="sxs-lookup"><span data-stu-id="042ec-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="042ec-119">Heslo</span><span class="sxs-lookup"><span data-stu-id="042ec-119">Password</span></span>|<span data-ttu-id="042ec-120">Ověření přenosu rovnocenného kanálu vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="042ec-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="042ec-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="042ec-121">Child Elements</span></span>  
 <span data-ttu-id="042ec-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="042ec-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="042ec-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="042ec-123">Parent Elements</span></span>  
  
|<span data-ttu-id="042ec-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="042ec-124">Element</span></span>|<span data-ttu-id="042ec-125">Description</span><span class="sxs-lookup"><span data-stu-id="042ec-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="042ec-126">Definuje nastavení zabezpečení pro [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="042ec-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="042ec-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="042ec-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="042ec-128">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="042ec-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="042ec-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="042ec-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="042ec-130">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="042ec-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="042ec-131">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="042ec-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
