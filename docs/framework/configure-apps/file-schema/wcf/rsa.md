---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: dd8e5ab11a7c019a8fe967f1c14b88a922a16c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934739"
---
# <a name="rsa"></a><span data-ttu-id="8f3eb-101">\<rsa></span><span class="sxs-lookup"><span data-stu-id="8f3eb-101">\<rsa></span></span>
<span data-ttu-id="8f3eb-102">Zabezpečený klient WCF, který se připojí ke koncovému bodu s touto identitou, ověří, že deklarace prezentované serverem obsahují deklaraci identity, která obsahuje veřejný klíč RSA používaný k vytvoření této identity.</span><span class="sxs-lookup"><span data-stu-id="8f3eb-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="8f3eb-103">\<> identity</span><span class="sxs-lookup"><span data-stu-id="8f3eb-103">\<identity></span></span>  
<span data-ttu-id="8f3eb-104">\<rsa></span><span class="sxs-lookup"><span data-stu-id="8f3eb-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f3eb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f3eb-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f3eb-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8f3eb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8f3eb-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8f3eb-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f3eb-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="8f3eb-108">Attributes</span></span>  
  
|<span data-ttu-id="8f3eb-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="8f3eb-109">Attribute</span></span>|<span data-ttu-id="8f3eb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8f3eb-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f3eb-111">value</span><span class="sxs-lookup"><span data-stu-id="8f3eb-111">value</span></span>|<span data-ttu-id="8f3eb-112">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="8f3eb-112">Optional String.</span></span> <span data-ttu-id="8f3eb-113">Hodnota veřejného klíče RSA, která má být porovnána s klientem.</span><span class="sxs-lookup"><span data-stu-id="8f3eb-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f3eb-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8f3eb-114">Child Elements</span></span>  
 <span data-ttu-id="8f3eb-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="8f3eb-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f3eb-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8f3eb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8f3eb-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="8f3eb-117">Element</span></span>|<span data-ttu-id="8f3eb-118">Popis</span><span class="sxs-lookup"><span data-stu-id="8f3eb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f3eb-119">\<identity></span><span class="sxs-lookup"><span data-stu-id="8f3eb-119">\<identity></span></span>](identity.md)|<span data-ttu-id="8f3eb-120">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="8f3eb-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f3eb-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f3eb-121">Remarks</span></span>  
 <span data-ttu-id="8f3eb-122">Pomocí kontroly RSA můžete výslovně omezit ověřování na jeden certifikát na základě jeho klíče RSA nebo vygenerovat vlastní hodnotu klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="8f3eb-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="8f3eb-123">To umožňuje striktní ověřování konkrétního klíče RSA za cenu služby, která už nepracuje se stávajícími klienty, pokud se změní hodnota klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="8f3eb-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="8f3eb-124">Další informace o použití identity k ověření služby klientovi najdete v tématu [identita služby a ověřování](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8f3eb-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f3eb-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f3eb-125">Example</span></span>  
 <span data-ttu-id="8f3eb-126">Následující konfigurační kód určuje hodnotu veřejného klíče certifikátu X. 509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="8f3eb-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="8f3eb-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f3eb-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="8f3eb-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="8f3eb-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="8f3eb-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="8f3eb-129">\<identity></span></span>](identity.md)
