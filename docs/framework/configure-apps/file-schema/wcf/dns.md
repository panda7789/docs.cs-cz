---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: c68cabd03eca71b41a0d0acce26897fa2653f4d3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855376"
---
# <a name="dns"></a><span data-ttu-id="e4091-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="e4091-101">\<dns></span></span>
<span data-ttu-id="e4091-102">Určuje očekávanou identitu serveru.</span><span class="sxs-lookup"><span data-stu-id="e4091-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="e4091-103">Tato identita je platná pro režim ověřování certifikátu x509, pokud certifikát serveru obsahuje DNS se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="e4091-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="e4091-104">Je také platný pro režim ověřování systému Windows, pokud má hlavní název služby stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e4091-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="e4091-105">Další informace o nastavení hodnoty prvku naleznete v tématu [identity a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e4091-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="e4091-106">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e4091-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e4091-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e4091-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e4091-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="e4091-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="e4091-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="e4091-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="e4091-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identity**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="e4091-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="e4091-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> DNS**</span><span class="sxs-lookup"><span data-stu-id="e4091-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4091-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4091-112">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4091-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e4091-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e4091-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e4091-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4091-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4091-115">Attributes</span></span>  
  
|<span data-ttu-id="e4091-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4091-116">Attribute</span></span>|<span data-ttu-id="e4091-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e4091-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4091-118">value</span><span class="sxs-lookup"><span data-stu-id="e4091-118">value</span></span>|<span data-ttu-id="e4091-119">DNS certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e4091-119">The DNS of the certificate.</span></span> <span data-ttu-id="e4091-120">DNS je standardní protokol, který se používá k nalezení počítačů v síti založené na protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="e4091-120">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="e4091-121">Uživatelé si můžou pamatovat zobrazované názvy, <https://go.microsoft.com/fwlink/?prd=10929> například [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165)nebo, jednodušší než adresy založené na číslech, jako je například 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="e4091-121">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4091-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e4091-122">Child Elements</span></span>  
 <span data-ttu-id="e4091-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="e4091-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4091-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e4091-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e4091-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4091-125">Element</span></span>|<span data-ttu-id="e4091-126">Popis</span><span class="sxs-lookup"><span data-stu-id="e4091-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4091-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="e4091-127">\<identity></span></span>](identity.md)|<span data-ttu-id="e4091-128">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="e4091-128">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e4091-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4091-129">Example</span></span>  
 <span data-ttu-id="e4091-130">Následující konfigurační kód určuje DNS certifikátu X. 509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="e4091-130">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="e4091-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4091-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="e4091-132">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="e4091-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e4091-133">\<identity></span><span class="sxs-lookup"><span data-stu-id="e4091-133">\<identity></span></span>](identity.md)
