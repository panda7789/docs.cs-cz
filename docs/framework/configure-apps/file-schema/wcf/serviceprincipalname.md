---
title: '&lt;servicePrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e472c7fcfd57341074489a75f7954be38291523b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltserviceprincipalnamegt"></a><span data-ttu-id="a972e-102">&lt;servicePrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="a972e-102">&lt;servicePrincipalName&gt;</span></span>
<span data-ttu-id="a972e-103">Určuje identity služby podle jeho hlavní název služby (SPN).</span><span class="sxs-lookup"><span data-stu-id="a972e-103">Specifies the identity of a service by its Service Principal Name (SPN).</span></span>  
  
 <span data-ttu-id="a972e-104">Další informace o nastavení hlavního názvu služby najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a972e-104">For more information about setting the SPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="a972e-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="a972e-105">\<identity></span></span>  
<span data-ttu-id="a972e-106">\<servicePrincipalName ></span><span class="sxs-lookup"><span data-stu-id="a972e-106">\<servicePrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a972e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a972e-107">Syntax</span></span>  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a972e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a972e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a972e-109">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a972e-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a972e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a972e-110">Attributes</span></span>  
  
|<span data-ttu-id="a972e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a972e-111">Attribute</span></span>|<span data-ttu-id="a972e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a972e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a972e-113">value</span><span class="sxs-lookup"><span data-stu-id="a972e-113">value</span></span>|<span data-ttu-id="a972e-114">Název, podle kterého klient jednoznačně identifikuje instance služby.</span><span class="sxs-lookup"><span data-stu-id="a972e-114">The name by which a client uniquely identifies an instance of a service.</span></span> <span data-ttu-id="a972e-115">Pokud instalujete více instancí služby v počítačích v rámci doménové struktury, každá instance musí mít svůj vlastní název SPN.</span><span class="sxs-lookup"><span data-stu-id="a972e-115">If you install multiple instances of a service on computers throughout a forest, each instance must have its own SPN.</span></span> <span data-ttu-id="a972e-116">Instance dané služby může mít několik SPN, pokud existuje více názvů, které můžou klienti používat pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="a972e-116">A given service instance can have multiple SPNs if there are multiple names that clients might use for authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a972e-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a972e-117">Child Elements</span></span>  
 <span data-ttu-id="a972e-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="a972e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a972e-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a972e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a972e-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="a972e-120">Element</span></span>|<span data-ttu-id="a972e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="a972e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a972e-122">\<identity ></span><span class="sxs-lookup"><span data-stu-id="a972e-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="a972e-123">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="a972e-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a972e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a972e-124">Remarks</span></span>  
 <span data-ttu-id="a972e-125">Zabezpečený [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klienta, která se připojuje k koncový bod s tuto identitu používá SPN při ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="a972e-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the SPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a972e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a972e-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [<span data-ttu-id="a972e-127">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="a972e-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a972e-128">\<identity ></span><span class="sxs-lookup"><span data-stu-id="a972e-128">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
