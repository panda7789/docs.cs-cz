---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e1651f563bdb2b2b24eacacf7bfe387e33a82c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855043"
---
# \<rsa>
<span data-ttu-id="c418a-101">Zabezpečený klient WCF, který se připojí ke koncovému bodu s touto identitou, ověří, že deklarace prezentované serverem obsahují deklaraci identity, která obsahuje veřejný klíč RSA používaný k vytvoření této identity.</span><span class="sxs-lookup"><span data-stu-id="c418a-101">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<rsa>**  
  
## <a name="syntax"></a><span data-ttu-id="c418a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c418a-102">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c418a-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c418a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c418a-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c418a-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c418a-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="c418a-105">Attributes</span></span>  
  
|<span data-ttu-id="c418a-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="c418a-106">Attribute</span></span>|<span data-ttu-id="c418a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c418a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c418a-108">hodnota</span><span class="sxs-lookup"><span data-stu-id="c418a-108">value</span></span>|<span data-ttu-id="c418a-109">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c418a-109">Optional String.</span></span> <span data-ttu-id="c418a-110">Hodnota veřejného klíče RSA, která má být porovnána s klientem.</span><span class="sxs-lookup"><span data-stu-id="c418a-110">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c418a-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c418a-111">Child Elements</span></span>  
 <span data-ttu-id="c418a-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="c418a-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c418a-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c418a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c418a-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="c418a-114">Element</span></span>|<span data-ttu-id="c418a-115">Description</span><span class="sxs-lookup"><span data-stu-id="c418a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="c418a-116">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="c418a-116">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c418a-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c418a-117">Remarks</span></span>  
 <span data-ttu-id="c418a-118">Pomocí kontroly RSA můžete výslovně omezit ověřování na jeden certifikát na základě jeho klíče RSA nebo vygenerovat vlastní hodnotu klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="c418a-118">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="c418a-119">To umožňuje striktní ověřování konkrétního klíče RSA za cenu služby, která už nepracuje se stávajícími klienty, pokud se změní hodnota klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="c418a-119">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="c418a-120">Další informace o použití identity k ověření služby klientovi najdete v tématu [identita služby a ověřování](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c418a-120">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c418a-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="c418a-121">Example</span></span>  
 <span data-ttu-id="c418a-122">Následující konfigurační kód určuje hodnotu veřejného klíče certifikátu X. 509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="c418a-122">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c418a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c418a-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="c418a-124">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="c418a-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
