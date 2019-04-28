---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 26b45b17ecd7bbd3fffb5d03553834ec22eedc62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700927"
---
# <a name="dns"></a><span data-ttu-id="6aff3-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="6aff3-101">\<dns></span></span>
<span data-ttu-id="6aff3-102">Určuje očekávanou identitu serveru.</span><span class="sxs-lookup"><span data-stu-id="6aff3-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="6aff3-103">Tato identita je platný pro X509 režim ověřování certifikátu, pokud certifikát serveru obsahuje DNS se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="6aff3-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="6aff3-104">Platí také pro režim ověřování systému Windows Pokud hlavní název služby má stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6aff3-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="6aff3-105">Další informace o nastavení hodnoty prvku naleznete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6aff3-105">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="6aff3-106">\<identity></span><span class="sxs-lookup"><span data-stu-id="6aff3-106">\<identity></span></span>  
<span data-ttu-id="6aff3-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="6aff3-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aff3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6aff3-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6aff3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6aff3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6aff3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6aff3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6aff3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6aff3-111">Attributes</span></span>  
  
|<span data-ttu-id="6aff3-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="6aff3-112">Attribute</span></span>|<span data-ttu-id="6aff3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6aff3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6aff3-114">value</span><span class="sxs-lookup"><span data-stu-id="6aff3-114">value</span></span>|<span data-ttu-id="6aff3-115">DNS certifikátu.</span><span class="sxs-lookup"><span data-stu-id="6aff3-115">The DNS of the certificate.</span></span> <span data-ttu-id="6aff3-116">DNS je standardní protokol slouží k vyhledání počítačů v síti na základě IP adresy.</span><span class="sxs-lookup"><span data-stu-id="6aff3-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="6aff3-117">Uživatelé zapamatujete zobrazované názvy, například <https://go.microsoft.com/fwlink/?prd=10929> nebo [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), jednodušší než adres na základě čísla, jako je například 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="6aff3-117">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6aff3-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6aff3-118">Child Elements</span></span>  
 <span data-ttu-id="6aff3-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="6aff3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6aff3-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6aff3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6aff3-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="6aff3-121">Element</span></span>|<span data-ttu-id="6aff3-122">Popis</span><span class="sxs-lookup"><span data-stu-id="6aff3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6aff3-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="6aff3-123">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="6aff3-124">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="6aff3-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6aff3-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="6aff3-125">Example</span></span>  
 <span data-ttu-id="6aff3-126">Následující kód konfigurace určuje DNS certifikát X.509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="6aff3-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="6aff3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6aff3-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="6aff3-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="6aff3-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6aff3-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="6aff3-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
