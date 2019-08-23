---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: 28ae27481ea9cb86c31b5be1f12b5491f8ca143e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936156"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="e89a7-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="e89a7-101">\<servicePrincipalName></span></span>
<span data-ttu-id="e89a7-102">Určuje identitu služby podle hlavního názvu služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="e89a7-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="e89a7-103">Další informace o nastavení hlavního názvu služby (SPN) najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e89a7-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="e89a7-104">\<> identity</span><span class="sxs-lookup"><span data-stu-id="e89a7-104">\<identity></span></span>  
<span data-ttu-id="e89a7-105">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="e89a7-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e89a7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e89a7-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e89a7-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e89a7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e89a7-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e89a7-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e89a7-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="e89a7-109">Attributes</span></span>  
  
|<span data-ttu-id="e89a7-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="e89a7-110">Attribute</span></span>|<span data-ttu-id="e89a7-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e89a7-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e89a7-112">value</span><span class="sxs-lookup"><span data-stu-id="e89a7-112">value</span></span>|<span data-ttu-id="e89a7-113">Název, kterým klient jednoznačně identifikuje instanci služby.</span><span class="sxs-lookup"><span data-stu-id="e89a7-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="e89a7-114">Pokud instalujete více instancí služby na počítačích v rámci doménové struktury, každá instance musí mít vlastní hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="e89a7-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="e89a7-115">Pokud existuje více názvů, které mohou klienti použít k ověřování, může mít daná instance služby více názvů SPN.</span><span class="sxs-lookup"><span data-stu-id="e89a7-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e89a7-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e89a7-116">Child Elements</span></span>  
 <span data-ttu-id="e89a7-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="e89a7-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e89a7-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e89a7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e89a7-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="e89a7-119">Element</span></span>|<span data-ttu-id="e89a7-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e89a7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e89a7-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="e89a7-121">\<identity></span></span>](identity.md)|<span data-ttu-id="e89a7-122">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="e89a7-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e89a7-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e89a7-123">Remarks</span></span>  
 <span data-ttu-id="e89a7-124">Klient zabezpečeného Windows Communication Foundation (WCF), který se připojuje ke koncovému bodu s touto identitou, používá hlavní název služby (SPN) při provádění ověřování SSPI s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="e89a7-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89a7-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e89a7-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="e89a7-126">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="e89a7-126">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e89a7-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="e89a7-127">\<identity></span></span>](identity.md)
