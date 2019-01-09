---
title: '&lt;servicePrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: a22a905744980d0b370023e6236734a9bb0d6357
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150633"
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="14b76-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="14b76-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="14b76-103">Určuje identitu služby podle jeho hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="14b76-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="14b76-104">Další informace o nastavení hlavního názvu služby naleznete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="14b76-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="14b76-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="14b76-105">\<identity></span></span>  
<span data-ttu-id="14b76-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="14b76-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14b76-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14b76-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14b76-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="14b76-108">Attributes and Elements</span></span>  
 <span data-ttu-id="14b76-109">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="14b76-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14b76-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="14b76-110">Attributes</span></span>  
  
|<span data-ttu-id="14b76-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="14b76-111">Attribute</span></span>|<span data-ttu-id="14b76-112">Popis</span><span class="sxs-lookup"><span data-stu-id="14b76-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14b76-113">value</span><span class="sxs-lookup"><span data-stu-id="14b76-113">value</span></span>|<span data-ttu-id="14b76-114">Název, kterým klient jednoznačně identifikuje instanci služby.</span><span class="sxs-lookup"><span data-stu-id="14b76-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="14b76-115">Pokud více instancí služby nainstalovat v počítačích v rámci doménové struktury, každá instance musí mít svůj vlastní hlavní název služby.</span><span class="sxs-lookup"><span data-stu-id="14b76-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="14b76-116">Uvedená služba instance může mít několik hlavních názvů služby, pokud existuje více názvů, které můžou klienti používat pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="14b76-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14b76-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="14b76-117">Child Elements</span></span>  
 <span data-ttu-id="14b76-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="14b76-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14b76-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="14b76-119">Parent Elements</span></span>  
  
|<span data-ttu-id="14b76-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="14b76-120">Element</span></span>|<span data-ttu-id="14b76-121">Popis</span><span class="sxs-lookup"><span data-stu-id="14b76-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14b76-122">\<identity ></span><span class="sxs-lookup"><span data-stu-id="14b76-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="14b76-123">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="14b76-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14b76-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14b76-124">Remarks</span></span>  
 <span data-ttu-id="14b76-125">Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tuto identitu použije hlavní název služby při provádění ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="14b76-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b76-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="14b76-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="14b76-127">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="14b76-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="14b76-128">\<identity ></span><span class="sxs-lookup"><span data-stu-id="14b76-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
