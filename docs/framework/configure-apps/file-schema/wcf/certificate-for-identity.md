---
title: <certificate> pro <identity>
ms.date: 03/30/2017
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
ms.openlocfilehash: 1cfd207afc72cc71359d9d262e30b0696ba63d2b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850015"
---
# <a name="certificate-for-identity"></a><span data-ttu-id="10ca6-102">\<> certifikátu pro \<> identity</span><span class="sxs-lookup"><span data-stu-id="10ca6-102">\<certificate> for \<identity></span></span>
<span data-ttu-id="10ca6-103">Určuje certifikát X. 509, který se používá k ověření serveru pro klienta.</span><span class="sxs-lookup"><span data-stu-id="10ca6-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
<span data-ttu-id="10ca6-104">Další informace o nastavení hodnoty prvku naleznete v tématu [identity a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="10ca6-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="10ca6-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="10ca6-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="10ca6-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="10ca6-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="10ca6-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="10ca6-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="10ca6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="10ca6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="10ca6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identity**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="10ca6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="10ca6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> certifikátu**</span><span class="sxs-lookup"><span data-stu-id="10ca6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10ca6-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10ca6-111">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10ca6-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="10ca6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="10ca6-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="10ca6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10ca6-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="10ca6-114">Attributes</span></span>  
  
|<span data-ttu-id="10ca6-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="10ca6-115">Attribute</span></span>|<span data-ttu-id="10ca6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="10ca6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10ca6-117">encodedValue</span><span class="sxs-lookup"><span data-stu-id="10ca6-117">encodedValue</span></span>|<span data-ttu-id="10ca6-118">Kódování Base64 certifikátu.</span><span class="sxs-lookup"><span data-stu-id="10ca6-118">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10ca6-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="10ca6-119">Child Elements</span></span>  
 <span data-ttu-id="10ca6-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="10ca6-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10ca6-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="10ca6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="10ca6-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="10ca6-122">Element</span></span>|<span data-ttu-id="10ca6-123">Popis</span><span class="sxs-lookup"><span data-stu-id="10ca6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10ca6-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="10ca6-124">\<identity></span></span>](identity.md)|<span data-ttu-id="10ca6-125">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="10ca6-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="10ca6-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="10ca6-126">Example</span></span>  
 <span data-ttu-id="10ca6-127">Následující kód určuje zakódovaný reprezentace certifikátu používaného k ověření serveru klientovi.</span><span class="sxs-lookup"><span data-stu-id="10ca6-127">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="10ca6-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10ca6-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.EndpointIdentity>
- [<span data-ttu-id="10ca6-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="10ca6-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="10ca6-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="10ca6-130">\<identity></span></span>](identity.md)
