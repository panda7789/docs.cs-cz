---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: ba1484644c57651fc0feadcc61d71d03eec1899b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254918"
---
# <a name="serviceprincipalname"></a><span data-ttu-id="ab0be-101">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="ab0be-101">\<servicePrincipalName></span></span>
<span data-ttu-id="ab0be-102">Určuje identitu služby podle jeho hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="ab0be-102">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="ab0be-103">Další informace o nastavení hlavního názvu služby naleznete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ab0be-103">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="ab0be-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="ab0be-104">\<identity></span></span>  
<span data-ttu-id="ab0be-105">\<servicePrincipalName></span><span class="sxs-lookup"><span data-stu-id="ab0be-105">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab0be-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab0be-106">Syntax</span></span>  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab0be-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ab0be-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ab0be-108">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab0be-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab0be-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="ab0be-109">Attributes</span></span>  
  
|<span data-ttu-id="ab0be-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="ab0be-110">Attribute</span></span>|<span data-ttu-id="ab0be-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ab0be-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab0be-112">value</span><span class="sxs-lookup"><span data-stu-id="ab0be-112">value</span></span>|<span data-ttu-id="ab0be-113">Název, kterým klient jednoznačně identifikuje instanci služby.</span><span class="sxs-lookup"><span data-stu-id="ab0be-113">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="ab0be-114">Pokud více instancí služby nainstalovat v počítačích v rámci doménové struktury, každá instance musí mít svůj vlastní hlavní název služby.</span><span class="sxs-lookup"><span data-stu-id="ab0be-114">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="ab0be-115">Uvedená služba instance může mít několik hlavních názvů služby, pokud existuje více názvů, které můžou klienti používat pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="ab0be-115">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab0be-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ab0be-116">Child Elements</span></span>  
 <span data-ttu-id="ab0be-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="ab0be-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab0be-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ab0be-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ab0be-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="ab0be-119">Element</span></span>|<span data-ttu-id="ab0be-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ab0be-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab0be-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="ab0be-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="ab0be-122">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="ab0be-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab0be-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ab0be-123">Remarks</span></span>  
 <span data-ttu-id="ab0be-124">Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tuto identitu použije hlavní název služby při provádění ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="ab0be-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0be-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab0be-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [<span data-ttu-id="ab0be-126">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="ab0be-126">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="ab0be-127">\<identity></span><span class="sxs-lookup"><span data-stu-id="ab0be-127">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
