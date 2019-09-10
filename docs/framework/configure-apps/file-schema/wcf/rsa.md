---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855043"
---
# <a name="rsa"></a><span data-ttu-id="580ae-101">\<rsa></span><span class="sxs-lookup"><span data-stu-id="580ae-101">\<rsa></span></span>
<span data-ttu-id="580ae-102">Zabezpečený klient WCF, který se připojí ke koncovému bodu s touto identitou, ověří, že deklarace prezentované serverem obsahují deklaraci identity, která obsahuje veřejný klíč RSA používaný k vytvoření této identity.</span><span class="sxs-lookup"><span data-stu-id="580ae-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
<span data-ttu-id="580ae-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="580ae-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="580ae-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="580ae-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="580ae-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="580ae-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="580ae-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="580ae-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="580ae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identity**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="580ae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="580ae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> RSA**</span><span class="sxs-lookup"><span data-stu-id="580ae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="580ae-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="580ae-109">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="580ae-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="580ae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="580ae-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="580ae-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="580ae-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="580ae-112">Attributes</span></span>  
  
|<span data-ttu-id="580ae-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="580ae-113">Attribute</span></span>|<span data-ttu-id="580ae-114">Popis</span><span class="sxs-lookup"><span data-stu-id="580ae-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="580ae-115">value</span><span class="sxs-lookup"><span data-stu-id="580ae-115">value</span></span>|<span data-ttu-id="580ae-116">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="580ae-116">Optional String.</span></span> <span data-ttu-id="580ae-117">Hodnota veřejného klíče RSA, která má být porovnána s klientem.</span><span class="sxs-lookup"><span data-stu-id="580ae-117">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="580ae-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="580ae-118">Child Elements</span></span>  
 <span data-ttu-id="580ae-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="580ae-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="580ae-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="580ae-120">Parent Elements</span></span>  
  
|<span data-ttu-id="580ae-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="580ae-121">Element</span></span>|<span data-ttu-id="580ae-122">Popis</span><span class="sxs-lookup"><span data-stu-id="580ae-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="580ae-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="580ae-123">\<identity></span></span>](identity.md)|<span data-ttu-id="580ae-124">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="580ae-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="580ae-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="580ae-125">Remarks</span></span>  
 <span data-ttu-id="580ae-126">Pomocí kontroly RSA můžete výslovně omezit ověřování na jeden certifikát na základě jeho klíče RSA nebo vygenerovat vlastní hodnotu klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="580ae-126">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="580ae-127">To umožňuje striktní ověřování konkrétního klíče RSA za cenu služby, která už nepracuje se stávajícími klienty, pokud se změní hodnota klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="580ae-127">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="580ae-128">Další informace o použití identity k ověření služby klientovi najdete v tématu [identita služby a ověřování](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="580ae-128">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="580ae-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="580ae-129">Example</span></span>  
 <span data-ttu-id="580ae-130">Následující konfigurační kód určuje hodnotu veřejného klíče certifikátu X. 509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="580ae-130">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="580ae-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="580ae-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="580ae-132">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="580ae-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="580ae-133">\<identity></span><span class="sxs-lookup"><span data-stu-id="580ae-133">\<identity></span></span>](identity.md)
