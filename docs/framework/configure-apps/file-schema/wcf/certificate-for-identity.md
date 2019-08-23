---
title: <certificate> pro <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 52d1fa31cebd949c91809464976739ef1334af29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919618"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="7e1fc-102">\<> certifikátu pro \<> identity</span><span class="sxs-lookup"><span data-stu-id="7e1fc-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="7e1fc-103">Určuje certifikát X. 509, který se používá k ověření serveru pro klienta.</span><span class="sxs-lookup"><span data-stu-id="7e1fc-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="7e1fc-104">Další informace o nastavení hodnoty prvku naleznete v tématu [identity a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7e1fc-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="7e1fc-105">\<> identity</span><span class="sxs-lookup"><span data-stu-id="7e1fc-105">\<identity></span></span>  
<span data-ttu-id="7e1fc-106">\<> certifikátu</span><span class="sxs-lookup"><span data-stu-id="7e1fc-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e1fc-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e1fc-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e1fc-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7e1fc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7e1fc-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7e1fc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e1fc-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7e1fc-110">Attributes</span></span>  
  
|<span data-ttu-id="7e1fc-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="7e1fc-111">Attribute</span></span>|<span data-ttu-id="7e1fc-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7e1fc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7e1fc-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="7e1fc-113">encodedValue</span></span>|<span data-ttu-id="7e1fc-114">Kódování Base64 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="7e1fc-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e1fc-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7e1fc-115">Child Elements</span></span>  
 <span data-ttu-id="7e1fc-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="7e1fc-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e1fc-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7e1fc-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7e1fc-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="7e1fc-118">Element</span></span>|<span data-ttu-id="7e1fc-119">Popis</span><span class="sxs-lookup"><span data-stu-id="7e1fc-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e1fc-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="7e1fc-120">\<identity></span></span>](identity.md)|<span data-ttu-id="7e1fc-121">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="7e1fc-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7e1fc-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e1fc-122">Example</span></span>  
 <span data-ttu-id="7e1fc-123">Následující kód určuje zakódovaný reprezentace certifikátu používaného k ověření serveru klientovi.</span><span class="sxs-lookup"><span data-stu-id="7e1fc-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="7e1fc-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e1fc-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="7e1fc-125">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="7e1fc-125">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7e1fc-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="7e1fc-126">\<identity></span></span>](identity.md)
