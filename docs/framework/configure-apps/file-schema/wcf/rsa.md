---
title: <rsa>
ms.date: 03/30/2017
ms.assetid: ae1f2267-e40d-42ff-8abf-06ab7067bdb9
ms.openlocfilehash: 0e307069bd3a98153cc66147ba7bcf511cf13a8e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091652"
---
# <a name="rsa"></a><span data-ttu-id="a768b-101">\<rsa></span><span class="sxs-lookup"><span data-stu-id="a768b-101">\<rsa></span></span>
<span data-ttu-id="a768b-102">Zabezpečené klienta WCF, která se připojuje k koncový bod s tuto identitu ověří, deklarací identity předkládaných server obsahovat deklaraci identity, který obsahuje veřejný klíč RSA použitý k vytvoření této identity.</span><span class="sxs-lookup"><span data-stu-id="a768b-102">A secure WCF client that connects to an endpoint with this identity verifies that the claims presented by the server contain a claim that contains the RSA public key used to construct this identity.</span></span>  
  
 <span data-ttu-id="a768b-103">\<identity></span><span class="sxs-lookup"><span data-stu-id="a768b-103">\<identity></span></span>  
<span data-ttu-id="a768b-104">\<rsa></span><span class="sxs-lookup"><span data-stu-id="a768b-104">\<rsa></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a768b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a768b-105">Syntax</span></span>  
  
```xml  
<rsa value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a768b-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a768b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a768b-107">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a768b-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a768b-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="a768b-108">Attributes</span></span>  
  
|<span data-ttu-id="a768b-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="a768b-109">Attribute</span></span>|<span data-ttu-id="a768b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a768b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a768b-111">value</span><span class="sxs-lookup"><span data-stu-id="a768b-111">value</span></span>|<span data-ttu-id="a768b-112">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="a768b-112">Optional String.</span></span> <span data-ttu-id="a768b-113">RSA veřejné hodnota klíče, která bude porovnána na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="a768b-113">The RSA public key value to be compared with on the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a768b-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a768b-114">Child Elements</span></span>  
 <span data-ttu-id="a768b-115">Žádný</span><span class="sxs-lookup"><span data-stu-id="a768b-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a768b-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a768b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a768b-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="a768b-117">Element</span></span>|<span data-ttu-id="a768b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a768b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a768b-119">\<identity></span><span class="sxs-lookup"><span data-stu-id="a768b-119">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="a768b-120">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="a768b-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a768b-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a768b-121">Remarks</span></span>  
 <span data-ttu-id="a768b-122">Kontrolu RSA umožňuje konkrétně omezit ověřování do jednoho certifikátu na základě jeho klíč RSA nebo vygenerovat vlastní hodnotu klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="a768b-122">A RSA check enables you to specifically restrict authentication to a single certificate based upon its RSA key or generated your own RSA key value.</span></span> <span data-ttu-id="a768b-123">Toto umožňuje přísnější ověřování konkrétního klíče RSA za cenu služba již práce s existující klienti při změně hodnoty klíče RSA.</span><span class="sxs-lookup"><span data-stu-id="a768b-123">This enables stricter authentication of a specific RSA key at the expense of the service no longer working with existing clients if the RSA key value is changed.</span></span>  
  
 <span data-ttu-id="a768b-124">Další informace o používání identity k ověření služby ke klientovi naleznete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a768b-124">For more information about using identity to validate a service to a client, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a768b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="a768b-125">Example</span></span>  
 <span data-ttu-id="a768b-126">Následující kód konfigurace určuje hodnota veřejného klíče certifikátu X.509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="a768b-126">The following configuration code specifies the public key value of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <rsa value="0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="a768b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a768b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.RsaEndpointIdentity>
- [<span data-ttu-id="a768b-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="a768b-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a768b-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="a768b-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
