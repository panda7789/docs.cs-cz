---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23e2599920c0ef0ea35569ec9b0b16b0f8735f1a
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="13030-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="13030-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="13030-103">Určuje hlavní název uživatele (UPN) služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="13030-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="13030-104">Další informace o nastavení hlavního názvu uživatele najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="13030-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="13030-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="13030-105">\<identity></span></span>  
<span data-ttu-id="13030-106">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="13030-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13030-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13030-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13030-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="13030-108">Attributes and Elements</span></span>  
 <span data-ttu-id="13030-109">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="13030-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13030-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="13030-110">Attributes</span></span>  
  
|<span data-ttu-id="13030-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="13030-111">Attribute</span></span>|<span data-ttu-id="13030-112">Popis</span><span class="sxs-lookup"><span data-stu-id="13030-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13030-113">value</span><span class="sxs-lookup"><span data-stu-id="13030-113">value</span></span>|<span data-ttu-id="13030-114">Název uživatelského účtu (někdy označované jako přihlašovací jméno uživatele) a název domény určujícího doménu, ve kterém se nachází uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="13030-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="13030-115">Toto je standardní použití pro přihlášení k doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="13030-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="13030-116">Formát je: someone@example.com (jako u e-mailovou adresu).</span><span class="sxs-lookup"><span data-stu-id="13030-116">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13030-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="13030-117">Child Elements</span></span>  
 <span data-ttu-id="13030-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="13030-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13030-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="13030-119">Parent Elements</span></span>  
  
|<span data-ttu-id="13030-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="13030-120">Element</span></span>|<span data-ttu-id="13030-121">Popis</span><span class="sxs-lookup"><span data-stu-id="13030-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13030-122">\<identity ></span><span class="sxs-lookup"><span data-stu-id="13030-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="13030-123">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="13030-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13030-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13030-124">Remarks</span></span>  
 <span data-ttu-id="13030-125">Zabezpečený [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klienta, která se připojuje k koncový bod s tuto identitu používá název UPN při ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="13030-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13030-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="13030-126">Example</span></span>  
 <span data-ttu-id="13030-127">Následující kód konfigurace určuje UPN služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="13030-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13030-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="13030-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="13030-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="13030-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="13030-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="13030-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
