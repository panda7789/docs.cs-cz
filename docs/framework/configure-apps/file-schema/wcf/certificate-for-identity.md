---
title: <certificate> pro <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 76bdcb40d5016d7fcbff6c0d9769819f710065fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205833"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="e5642-102">\<certifikát > pro \<identity ></span><span class="sxs-lookup"><span data-stu-id="e5642-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="e5642-103">Určuje certifikát X.509 sloužící k ověření serveru do klienta.</span><span class="sxs-lookup"><span data-stu-id="e5642-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="e5642-104">Další informace o nastavení hodnoty prvku naleznete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e5642-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="e5642-105">\<identity></span><span class="sxs-lookup"><span data-stu-id="e5642-105">\<identity></span></span>  
<span data-ttu-id="e5642-106">\<certifikát ></span><span class="sxs-lookup"><span data-stu-id="e5642-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5642-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5642-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5642-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e5642-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e5642-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e5642-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5642-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e5642-110">Attributes</span></span>  
  
|<span data-ttu-id="e5642-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e5642-111">Attribute</span></span>|<span data-ttu-id="e5642-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e5642-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5642-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="e5642-113">encodedValue</span></span>|<span data-ttu-id="e5642-114">Kódování Base64 z certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e5642-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5642-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e5642-115">Child Elements</span></span>  
 <span data-ttu-id="e5642-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="e5642-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5642-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e5642-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e5642-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="e5642-118">Element</span></span>|<span data-ttu-id="e5642-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e5642-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5642-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="e5642-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e5642-121">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="e5642-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5642-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5642-122">Example</span></span>  
 <span data-ttu-id="e5642-123">Následující kód určuje kódovaného reprezentace certifikát používaný k ověření serveru do klienta.</span><span class="sxs-lookup"><span data-stu-id="e5642-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="e5642-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5642-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="e5642-125">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="e5642-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e5642-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="e5642-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
