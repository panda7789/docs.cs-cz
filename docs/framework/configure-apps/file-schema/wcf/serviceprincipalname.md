---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854989"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="cbc55-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="cbc55-101">\<servicePrincipalName></span></span>
<span data-ttu-id="cbc55-102">Určuje identitu služby podle hlavního názvu služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="cbc55-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
<span data-ttu-id="cbc55-103">Další informace o nastavení hlavního názvu služby (SPN) najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cbc55-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="cbc55-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cbc55-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cbc55-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cbc55-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cbc55-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="cbc55-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="cbc55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="cbc55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="cbc55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identity**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="cbc55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="cbc55-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> servicePrincipalName**</span><span class="sxs-lookup"><span data-stu-id="cbc55-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc55-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbc55-110">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbc55-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cbc55-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cbc55-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cbc55-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbc55-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="cbc55-113">Attributes</span></span>  
  
|<span data-ttu-id="cbc55-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="cbc55-114">Attribute</span></span>|<span data-ttu-id="cbc55-115">Popis</span><span class="sxs-lookup"><span data-stu-id="cbc55-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbc55-116">value</span><span class="sxs-lookup"><span data-stu-id="cbc55-116">value</span></span>|<span data-ttu-id="cbc55-117">Název, kterým klient jednoznačně identifikuje instanci služby.</span><span class="sxs-lookup"><span data-stu-id="cbc55-117">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="cbc55-118">Pokud instalujete více instancí služby na počítačích v rámci doménové struktury, každá instance musí mít vlastní hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="cbc55-118">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="cbc55-119">Pokud existuje více názvů, které mohou klienti použít k ověřování, může mít daná instance služby více názvů SPN.</span><span class="sxs-lookup"><span data-stu-id="cbc55-119">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbc55-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cbc55-120">Child Elements</span></span>  
 <span data-ttu-id="cbc55-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="cbc55-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbc55-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cbc55-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cbc55-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="cbc55-123">Element</span></span>|<span data-ttu-id="cbc55-124">Popis</span><span class="sxs-lookup"><span data-stu-id="cbc55-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbc55-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="cbc55-125">\<identity></span></span>](identity.md)|<span data-ttu-id="cbc55-126">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="cbc55-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbc55-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbc55-127">Remarks</span></span>  
 <span data-ttu-id="cbc55-128">Klient zabezpečeného Windows Communication Foundation (WCF), který se připojuje ke koncovému bodu s touto identitou, používá hlavní název služby (SPN) při provádění ověřování SSPI s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="cbc55-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc55-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbc55-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="cbc55-130">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="cbc55-130">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="cbc55-131">\<identity></span><span class="sxs-lookup"><span data-stu-id="cbc55-131">\<identity></span></span>](identity.md)
