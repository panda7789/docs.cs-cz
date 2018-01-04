---
title: '&lt;DNS&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c7585cfa85d805a3d1454b0c16e38eee297280a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdnsgt"></a><span data-ttu-id="02ba1-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="02ba1-102">&lt;dns&gt;</span></span>
<span data-ttu-id="02ba1-103">Určuje očekávanou identitu serveru.</span><span class="sxs-lookup"><span data-stu-id="02ba1-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="02ba1-104">Tato identita je platný pro X509 režim ověřování certifikátu, pokud certifikát serveru obsahuje DNS se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="02ba1-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="02ba1-105">Je taky platná pro režim ověřování systému Windows Pokud hlavní název služby má stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02ba1-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="02ba1-106">Další informace o nastavení hodnota elementu najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="02ba1-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="02ba1-107">\<identity ></span><span class="sxs-lookup"><span data-stu-id="02ba1-107">\<identity></span></span>  
<span data-ttu-id="02ba1-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="02ba1-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02ba1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02ba1-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02ba1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="02ba1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="02ba1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="02ba1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02ba1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="02ba1-112">Attributes</span></span>  
  
|<span data-ttu-id="02ba1-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="02ba1-113">Attribute</span></span>|<span data-ttu-id="02ba1-114">Popis</span><span class="sxs-lookup"><span data-stu-id="02ba1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02ba1-115">value</span><span class="sxs-lookup"><span data-stu-id="02ba1-115">value</span></span>|<span data-ttu-id="02ba1-116">DNS certifikátu.</span><span class="sxs-lookup"><span data-stu-id="02ba1-116">The DNS of the certificate.</span></span> <span data-ttu-id="02ba1-117">DNS je standardní protokol používaná k nalezení počítače v síti založenou na protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="02ba1-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="02ba1-118">Uživatelé pamatovat zobrazované názvy, například [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) nebo [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), jednodušší než adresy na základě číslo, například 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="02ba1-118">Users can remember display names, such as [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) or [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02ba1-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="02ba1-119">Child Elements</span></span>  
 <span data-ttu-id="02ba1-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="02ba1-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02ba1-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="02ba1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="02ba1-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="02ba1-122">Element</span></span>|<span data-ttu-id="02ba1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="02ba1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02ba1-124">\<identity ></span><span class="sxs-lookup"><span data-stu-id="02ba1-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="02ba1-125">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="02ba1-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="02ba1-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="02ba1-126">Example</span></span>  
 <span data-ttu-id="02ba1-127">Následující kód konfigurace určuje DNS certifikát X.509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="02ba1-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02ba1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="02ba1-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="02ba1-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="02ba1-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="02ba1-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="02ba1-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
