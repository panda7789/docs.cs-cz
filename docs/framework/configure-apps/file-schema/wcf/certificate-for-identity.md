---
title: <certificate>for<identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850015"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="fc2d0-102">\<certificate>for\<identity></span><span class="sxs-lookup"><span data-stu-id="fc2d0-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="fc2d0-103">Určuje certifikát X. 509, který se používá k ověření serveru pro klienta.</span><span class="sxs-lookup"><span data-stu-id="fc2d0-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="fc2d0-104">Další informace o nastavení hodnoty prvku naleznete v tématu [identity a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fc2d0-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="fc2d0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc2d0-105">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc2d0-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fc2d0-106">Attributes and Elements</span></span>  
 <span data-ttu-id="fc2d0-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fc2d0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc2d0-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="fc2d0-108">Attributes</span></span>  
  
|<span data-ttu-id="fc2d0-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="fc2d0-109">Attribute</span></span>|<span data-ttu-id="fc2d0-110">Popis</span><span class="sxs-lookup"><span data-stu-id="fc2d0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc2d0-111">encodedValue</span><span class="sxs-lookup"><span data-stu-id="fc2d0-111">encodedValue</span></span>|<span data-ttu-id="fc2d0-112">Kódování Base64 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="fc2d0-112">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc2d0-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fc2d0-113">Child Elements</span></span>  
 <span data-ttu-id="fc2d0-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="fc2d0-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc2d0-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fc2d0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="fc2d0-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc2d0-116">Element</span></span>|<span data-ttu-id="fc2d0-117">Description</span><span class="sxs-lookup"><span data-stu-id="fc2d0-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="fc2d0-118">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="fc2d0-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fc2d0-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc2d0-119">Example</span></span>  
 <span data-ttu-id="fc2d0-120">Následující kód určuje zakódovaný reprezentace certifikátu používaného k ověření serveru klientovi.</span><span class="sxs-lookup"><span data-stu-id="fc2d0-120">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="fc2d0-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc2d0-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="fc2d0-122">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="fc2d0-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
