---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452224"
---
# <a name="dns"></a><span data-ttu-id="86e18-101">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="86e18-101">\<dns></span></span>
<span data-ttu-id="86e18-102">Určuje očekávanou identitu serveru.</span><span class="sxs-lookup"><span data-stu-id="86e18-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="86e18-103">Tato identita je platná pro režim ověřování certifikátu x509, pokud certifikát serveru obsahuje DNS se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="86e18-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="86e18-104">Je také platný pro režim ověřování systému Windows, pokud má hlavní název služby stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="86e18-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="86e18-105">Další informace o nastavení hodnoty prvku naleznete v tématu [identity a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="86e18-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="86e18-106">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="86e18-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86e18-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="86e18-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="86e18-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<klient >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="86e18-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="86e18-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<koncový bod >** ](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="86e18-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="86e18-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identity >** ](identity.md)</span><span class="sxs-lookup"><span data-stu-id="86e18-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="86e18-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dns >**</span><span class="sxs-lookup"><span data-stu-id="86e18-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e18-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86e18-112">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86e18-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="86e18-113">Attributes and Elements</span></span>  
 <span data-ttu-id="86e18-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="86e18-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86e18-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="86e18-115">Attributes</span></span>  
  
|<span data-ttu-id="86e18-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="86e18-116">Attribute</span></span>|<span data-ttu-id="86e18-117">Popis</span><span class="sxs-lookup"><span data-stu-id="86e18-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86e18-118">hodnota</span><span class="sxs-lookup"><span data-stu-id="86e18-118">value</span></span>|<span data-ttu-id="86e18-119">DNS certifikátu.</span><span class="sxs-lookup"><span data-stu-id="86e18-119">The DNS of the certificate.</span></span> <span data-ttu-id="86e18-120">DNS je standardní protokol, který se používá k nalezení počítačů v síti založené na protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="86e18-120">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="86e18-121">Uživatelé si můžou pamatovat zobrazované názvy, například `https://go.microsoft.com/fwlink/?prd=10929` nebo `https://go.microsoft.com/fwlink/?LinkID=96165`, jednodušší než adresy založené na číslech, jako je například 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="86e18-121">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86e18-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="86e18-122">Child Elements</span></span>  
 <span data-ttu-id="86e18-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="86e18-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86e18-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="86e18-124">Parent Elements</span></span>  
  
|<span data-ttu-id="86e18-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="86e18-125">Element</span></span>|<span data-ttu-id="86e18-126">Popis</span><span class="sxs-lookup"><span data-stu-id="86e18-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86e18-127">\<> identity</span><span class="sxs-lookup"><span data-stu-id="86e18-127">\<identity></span></span>](identity.md)|<span data-ttu-id="86e18-128">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="86e18-128">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86e18-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="86e18-129">Example</span></span>  
 <span data-ttu-id="86e18-130">Následující konfigurační kód určuje DNS certifikátu X. 509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="86e18-130">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="86e18-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="86e18-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="86e18-132">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="86e18-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="86e18-133">\<> identity</span><span class="sxs-lookup"><span data-stu-id="86e18-133">\<identity></span></span>](identity.md)
