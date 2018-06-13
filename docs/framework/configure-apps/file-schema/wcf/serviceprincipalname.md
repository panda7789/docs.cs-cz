---
title: '&lt;ServicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: e5c1f5a6986d57d20180560b12f5c7c5540a590d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750723"
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="a6fe6-102">&lt;ServicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="a6fe6-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="a6fe6-103">Určuje identity služby podle jeho hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="a6fe6-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="a6fe6-104">Další informace o nastavení hlavního názvu služby najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a6fe6-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="a6fe6-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="a6fe6-105">\<identity></span></span>  
<span data-ttu-id="a6fe6-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="a6fe6-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6fe6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6fe6-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6fe6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a6fe6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a6fe6-109">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6fe6-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6fe6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a6fe6-110">Attributes</span></span>  
  
|<span data-ttu-id="a6fe6-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a6fe6-111">Attribute</span></span>|<span data-ttu-id="a6fe6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a6fe6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6fe6-113">value</span><span class="sxs-lookup"><span data-stu-id="a6fe6-113">value</span></span>|<span data-ttu-id="a6fe6-114">Název, podle kterého klient jednoznačně identifikuje instance služby.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="a6fe6-115">Pokud instalujete více instancí služby v počítačích v rámci doménové struktury, každá instance musí mít svůj vlastní název SPN.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="a6fe6-116">Instance dané služby může mít několik SPN, pokud existuje více názvů, které můžou klienti používat pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6fe6-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a6fe6-117">Child Elements</span></span>  
 <span data-ttu-id="a6fe6-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="a6fe6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6fe6-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a6fe6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a6fe6-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a6fe6-120">Element</span></span>|<span data-ttu-id="a6fe6-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a6fe6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6fe6-122">\<identity ></span><span class="sxs-lookup"><span data-stu-id="a6fe6-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="a6fe6-123">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6fe6-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6fe6-124">Remarks</span></span>  
 <span data-ttu-id="a6fe6-125">Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tuto identitu používá SPN při ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="a6fe6-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fe6-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6fe6-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="a6fe6-127">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="a6fe6-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a6fe6-128">\<identity ></span><span class="sxs-lookup"><span data-stu-id="a6fe6-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
