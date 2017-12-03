---
title: '&lt;certificate&gt; pro &lt;identity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d847def6268881cbd288fe9b3ba89de9403b41d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcertificategt-for-ltidentitygt"></a><span data-ttu-id="8d523-102">&lt;certificate&gt; pro &lt;identity&gt;</span><span class="sxs-lookup"><span data-stu-id="8d523-102">&lt;certificate&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="8d523-103">Určuje certifikátu X.509. certifikát použitý k ověření serveru ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="8d523-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="8d523-104">Další informace o nastavení hodnota elementu najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8d523-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="8d523-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="8d523-105">\<identity></span></span>  
<span data-ttu-id="8d523-106">\<certifikátu ></span><span class="sxs-lookup"><span data-stu-id="8d523-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d523-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d523-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d523-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8d523-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8d523-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8d523-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d523-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8d523-110">Attributes</span></span>  
  
|<span data-ttu-id="8d523-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8d523-111">Attribute</span></span>|<span data-ttu-id="8d523-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8d523-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d523-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="8d523-113">encodedValue</span></span>|<span data-ttu-id="8d523-114">Kódování Base64 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="8d523-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d523-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8d523-115">Child Elements</span></span>  
 <span data-ttu-id="8d523-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d523-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d523-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8d523-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8d523-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="8d523-118">Element</span></span>|<span data-ttu-id="8d523-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8d523-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d523-120">\<identity ></span><span class="sxs-lookup"><span data-stu-id="8d523-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="8d523-121">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="8d523-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8d523-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d523-122">Example</span></span>  
 <span data-ttu-id="8d523-123">Následující kód určuje vyjádření kódovaného certifikátu slouží k ověření serveru ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="8d523-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>  
  <certificate encodedValue = " MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d523-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d523-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.EndpointIdentity>  
 [<span data-ttu-id="8d523-125">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="8d523-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="8d523-126">\<identity ></span><span class="sxs-lookup"><span data-stu-id="8d523-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
