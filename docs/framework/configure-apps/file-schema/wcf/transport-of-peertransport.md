---
title: <transport> z <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399293"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="45c1a-102">\<transport> z \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="45c1a-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="45c1a-103">Určuje typ přenosu zabezpečených zpráv odesílaných partnerskými uzly nakonfigurovanými pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="45c1a-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="45c1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45c1a-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45c1a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="45c1a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="45c1a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="45c1a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45c1a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="45c1a-107">Attributes</span></span>  
  
|<span data-ttu-id="45c1a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="45c1a-108">Attribute</span></span>|<span data-ttu-id="45c1a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="45c1a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45c1a-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="45c1a-110">credentialType</span></span>|<span data-ttu-id="45c1a-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="45c1a-111">Optional.</span></span> <span data-ttu-id="45c1a-112">Určuje typ přihlašovacích údajů, které se používají k ověření zpráv odesílaných pomocí partnerského přenosu.</span><span class="sxs-lookup"><span data-stu-id="45c1a-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="45c1a-113">Tento atribut je typu <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="45c1a-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="45c1a-114">credentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="45c1a-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="45c1a-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="45c1a-115">Value</span></span>|<span data-ttu-id="45c1a-116">Description</span><span class="sxs-lookup"><span data-stu-id="45c1a-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45c1a-117">Certifikát</span><span class="sxs-lookup"><span data-stu-id="45c1a-117">Certificate</span></span>|<span data-ttu-id="45c1a-118">Ověřování přenosu rovnocenného kanálu vyžaduje certifikát x509.</span><span class="sxs-lookup"><span data-stu-id="45c1a-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="45c1a-119">Heslo</span><span class="sxs-lookup"><span data-stu-id="45c1a-119">Password</span></span>|<span data-ttu-id="45c1a-120">Ověření přenosu rovnocenného kanálu vyžaduje správné heslo.</span><span class="sxs-lookup"><span data-stu-id="45c1a-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45c1a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="45c1a-121">Child Elements</span></span>  
 <span data-ttu-id="45c1a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="45c1a-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45c1a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="45c1a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="45c1a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="45c1a-124">Element</span></span>|<span data-ttu-id="45c1a-125">Description</span><span class="sxs-lookup"><span data-stu-id="45c1a-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="45c1a-126">Definuje nastavení zabezpečení pro partnerský přenos.</span><span class="sxs-lookup"><span data-stu-id="45c1a-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45c1a-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45c1a-127">Remarks</span></span>  
 <span data-ttu-id="45c1a-128">Tento prvek je nastaven pouze v případě, že je atribut Mode [\<security>](security-of-peertransport.md) nastaven na `Transport` nebo `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="45c1a-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c1a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="45c1a-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="45c1a-130">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="45c1a-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="45c1a-131">Přenosy</span><span class="sxs-lookup"><span data-stu-id="45c1a-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="45c1a-132">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="45c1a-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="45c1a-133">Vazby</span><span class="sxs-lookup"><span data-stu-id="45c1a-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="45c1a-134">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="45c1a-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="45c1a-135">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="45c1a-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
