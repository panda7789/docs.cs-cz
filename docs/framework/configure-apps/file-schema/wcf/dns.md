---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77452224"
---
# \<dns>
<span data-ttu-id="c2b22-101">Určuje očekávanou identitu serveru.</span><span class="sxs-lookup"><span data-stu-id="c2b22-101">Specifies the expected identity of the server.</span></span> <span data-ttu-id="c2b22-102">Tato identita je platná pro režim ověřování certifikátu x509, pokud certifikát serveru obsahuje DNS se stejnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="c2b22-102">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="c2b22-103">Je také platný pro režim ověřování systému Windows, pokud má hlavní název služby stejnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c2b22-103">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="c2b22-104">Další informace o nastavení hodnoty prvku naleznete v tématu [identity a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c2b22-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="c2b22-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2b22-105">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2b22-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c2b22-106">Attributes and Elements</span></span>  
 <span data-ttu-id="c2b22-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c2b22-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2b22-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="c2b22-108">Attributes</span></span>  
  
|<span data-ttu-id="c2b22-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="c2b22-109">Attribute</span></span>|<span data-ttu-id="c2b22-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c2b22-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2b22-111">hodnota</span><span class="sxs-lookup"><span data-stu-id="c2b22-111">value</span></span>|<span data-ttu-id="c2b22-112">DNS certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c2b22-112">The DNS of the certificate.</span></span> <span data-ttu-id="c2b22-113">DNS je standardní protokol, který se používá k nalezení počítačů v síti založené na protokolu IP.</span><span class="sxs-lookup"><span data-stu-id="c2b22-113">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="c2b22-114">Uživatelé si můžou pamatovat zobrazované názvy, například `https://go.microsoft.com/fwlink/?prd=10929` nebo `https://go.microsoft.com/fwlink/?LinkID=96165` , jednodušší než adresy založené na číslech, jako je například 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="c2b22-114">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2b22-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c2b22-115">Child Elements</span></span>  
 <span data-ttu-id="c2b22-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2b22-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2b22-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c2b22-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c2b22-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2b22-118">Element</span></span>|<span data-ttu-id="c2b22-119">Description</span><span class="sxs-lookup"><span data-stu-id="c2b22-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="c2b22-120">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="c2b22-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c2b22-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2b22-121">Example</span></span>  
 <span data-ttu-id="c2b22-122">Následující konfigurační kód určuje DNS certifikátu X. 509, který se používá k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="c2b22-122">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="c2b22-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2b22-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="c2b22-124">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="c2b22-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
