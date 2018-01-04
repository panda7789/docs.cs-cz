---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34bfaeb563bd4979bf29a5e45a60730eb38700b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="7d0d3-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="7d0d3-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="7d0d3-103">Určuje hlavní název uživatele (UPN) služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="7d0d3-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="7d0d3-104">Další informace o nastavení hlavního názvu uživatele najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7d0d3-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="7d0d3-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="7d0d3-105">\<identity></span></span>  
<span data-ttu-id="7d0d3-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="7d0d3-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d0d3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d0d3-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d0d3-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d0d3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7d0d3-109">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d0d3-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d0d3-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d0d3-110">Attributes</span></span>  
  
|<span data-ttu-id="7d0d3-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="7d0d3-111">Attribute</span></span>|<span data-ttu-id="7d0d3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7d0d3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d0d3-113">value</span><span class="sxs-lookup"><span data-stu-id="7d0d3-113">value</span></span>|<span data-ttu-id="7d0d3-114">Název uživatelského účtu (někdy označované jako přihlašovací jméno uživatele) a název domény určujícího doménu, ve kterém se nachází uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="7d0d3-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="7d0d3-115">Toto je standardní použití pro přihlášení k doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7d0d3-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="7d0d3-116">Formát je: someone@example.com (jako u e-mailové adresy).</span><span class="sxs-lookup"><span data-stu-id="7d0d3-116">The format is: someone@example.com (as for an e-mail address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d0d3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d0d3-117">Child Elements</span></span>  
 <span data-ttu-id="7d0d3-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="7d0d3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d0d3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7d0d3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7d0d3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d0d3-120">Element</span></span>|<span data-ttu-id="7d0d3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="7d0d3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d0d3-122">\<identity ></span><span class="sxs-lookup"><span data-stu-id="7d0d3-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="7d0d3-123">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="7d0d3-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d0d3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d0d3-124">Remarks</span></span>  
 <span data-ttu-id="7d0d3-125">Zabezpečený [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klienta, která se připojuje k koncový bod s tuto identitu používá název UPN při ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="7d0d3-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d0d3-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d0d3-126">Example</span></span>  
 <span data-ttu-id="7d0d3-127">Následující kód konfigurace určuje UPN služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="7d0d3-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d0d3-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d0d3-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="7d0d3-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="7d0d3-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="7d0d3-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="7d0d3-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
