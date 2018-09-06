---
title: '&lt;DNS&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 2f5b9d5e1bc57230adbb32664e9ae15d3c71d46f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862475"
---
# <a name="ltdnsgt"></a><span data-ttu-id="1d665-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="1d665-102">&lt;dns&gt;</span></span>
<span data-ttu-id="1d665-103">Určuje očekávanou identitu serveru.</span><span class="sxs-lookup"><span data-stu-id="1d665-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="1d665-104">Tato identita je platný pro X509 režim ověřování certifikátu, pokud certifikát serveru obsahuje DNS se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="1d665-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="1d665-105">Platí také pro režim ověřování systému Windows Pokud hlavní název služby má stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1d665-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="1d665-106">Další informace o nastavení hodnoty prvku naleznete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1d665-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="1d665-107">\<identity ></span><span class="sxs-lookup"><span data-stu-id="1d665-107">\<identity></span></span>  
<span data-ttu-id="1d665-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="1d665-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d665-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d665-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d665-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1d665-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1d665-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1d665-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d665-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1d665-112">Attributes</span></span>  
  
|<span data-ttu-id="1d665-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1d665-113">Attribute</span></span>|<span data-ttu-id="1d665-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1d665-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1d665-115">value</span><span class="sxs-lookup"><span data-stu-id="1d665-115">value</span></span>|<span data-ttu-id="1d665-116">DNS certifikátu.</span><span class="sxs-lookup"><span data-stu-id="1d665-116">The DNS of the certificate.</span></span> <span data-ttu-id="1d665-117">DNS je standardní protokol slouží k vyhledání počítačů v síti na základě IP adresy.</span><span class="sxs-lookup"><span data-stu-id="1d665-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="1d665-118">Uživatelé zapamatujete zobrazované názvy, například [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) nebo [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), jednodušší než adres na základě čísla, jako je například 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="1d665-118">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d665-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1d665-119">Child Elements</span></span>  
 <span data-ttu-id="1d665-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="1d665-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d665-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1d665-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1d665-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d665-122">Element</span></span>|<span data-ttu-id="1d665-123">Popis</span><span class="sxs-lookup"><span data-stu-id="1d665-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d665-124">\<identity ></span><span class="sxs-lookup"><span data-stu-id="1d665-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="1d665-125">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="1d665-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1d665-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d665-126">Example</span></span>  
 <span data-ttu-id="1d665-127">Následující kód konfigurace určuje DNS certifikát X.509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="1d665-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d665-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d665-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="1d665-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="1d665-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="1d665-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="1d665-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
