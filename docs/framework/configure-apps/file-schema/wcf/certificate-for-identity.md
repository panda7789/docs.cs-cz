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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a9eabd25712136ef98f452cc15470bce1893527e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcertificategt-for-ltidentitygt"></a><span data-ttu-id="17616-102">&lt;certificate&gt; pro &lt;identity&gt;</span><span class="sxs-lookup"><span data-stu-id="17616-102">&lt;certificate&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="17616-103">Určuje certifikátu X.509. certifikát použitý k ověření serveru ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="17616-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="17616-104">Další informace o nastavení hodnota elementu najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="17616-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="17616-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="17616-105">\<identity></span></span>  
<span data-ttu-id="17616-106">\<certifikátu ></span><span class="sxs-lookup"><span data-stu-id="17616-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17616-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17616-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17616-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="17616-108">Attributes and Elements</span></span>  
 <span data-ttu-id="17616-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="17616-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17616-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="17616-110">Attributes</span></span>  
  
|<span data-ttu-id="17616-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="17616-111">Attribute</span></span>|<span data-ttu-id="17616-112">Popis</span><span class="sxs-lookup"><span data-stu-id="17616-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17616-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="17616-113">encodedValue</span></span>|<span data-ttu-id="17616-114">Kódování Base64 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="17616-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17616-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="17616-115">Child Elements</span></span>  
 <span data-ttu-id="17616-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="17616-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17616-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="17616-117">Parent Elements</span></span>  
  
|<span data-ttu-id="17616-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="17616-118">Element</span></span>|<span data-ttu-id="17616-119">Popis</span><span class="sxs-lookup"><span data-stu-id="17616-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17616-120">\<identity ></span><span class="sxs-lookup"><span data-stu-id="17616-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="17616-121">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="17616-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17616-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="17616-122">Example</span></span>  
 <span data-ttu-id="17616-123">Následující kód určuje vyjádření kódovaného certifikátu slouží k ověření serveru ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="17616-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>  
  <certificate encodedValue = " MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="17616-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="17616-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.EndpointIdentity>  
 [<span data-ttu-id="17616-125">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="17616-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="17616-126">\<identity ></span><span class="sxs-lookup"><span data-stu-id="17616-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
