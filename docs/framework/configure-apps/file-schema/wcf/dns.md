---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 35d33fd4d174c8e4ccdaaf1ac33884663340e16a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919127"
---
# <a name="dns"></a><span data-ttu-id="f9f8b-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="f9f8b-101">\<dns></span></span>
<span data-ttu-id="f9f8b-102">Určuje očekávanou identitu serveru.</span><span class="sxs-lookup"><span data-stu-id="f9f8b-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="f9f8b-103">Tato identita je platná pro režim ověřování certifikátu x509, pokud certifikát serveru obsahuje DNS se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="f9f8b-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="f9f8b-104">Je také platný pro režim ověřování systému Windows, pokud má hlavní název služby stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f9f8b-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="f9f8b-105">Další informace o nastavení hodnoty prvku naleznete v tématu [identity a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f9f8b-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="f9f8b-106">\<> identity</span><span class="sxs-lookup"><span data-stu-id="f9f8b-106">\<identity></span></span>  
<span data-ttu-id="f9f8b-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="f9f8b-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9f8b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9f8b-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9f8b-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f9f8b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f9f8b-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f9f8b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9f8b-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f9f8b-111">Attributes</span></span>  
  
|<span data-ttu-id="f9f8b-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="f9f8b-112">Attribute</span></span>|<span data-ttu-id="f9f8b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f9f8b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9f8b-114">value</span><span class="sxs-lookup"><span data-stu-id="f9f8b-114">value</span></span>|<span data-ttu-id="f9f8b-115">DNS certifikátu.</span><span class="sxs-lookup"><span data-stu-id="f9f8b-115">The DNS of the certificate.</span></span> <span data-ttu-id="f9f8b-116">DNS je standardní protokol, který se používá k nalezení počítačů v síti založené na protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="f9f8b-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="f9f8b-117">Uživatelé si můžou pamatovat zobrazované názvy, <https://go.microsoft.com/fwlink/?prd=10929> například [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165)nebo, jednodušší než adresy založené na číslech, jako je například 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="f9f8b-117">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9f8b-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f9f8b-118">Child Elements</span></span>  
 <span data-ttu-id="f9f8b-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="f9f8b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9f8b-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f9f8b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f9f8b-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f9f8b-121">Element</span></span>|<span data-ttu-id="f9f8b-122">Popis</span><span class="sxs-lookup"><span data-stu-id="f9f8b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9f8b-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="f9f8b-123">\<identity></span></span>](identity.md)|<span data-ttu-id="f9f8b-124">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="f9f8b-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f9f8b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9f8b-125">Example</span></span>  
 <span data-ttu-id="f9f8b-126">Následující konfigurační kód určuje DNS certifikátu X. 509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="f9f8b-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="f9f8b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9f8b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="f9f8b-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="f9f8b-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="f9f8b-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="f9f8b-129">\<identity></span></span>](identity.md)
