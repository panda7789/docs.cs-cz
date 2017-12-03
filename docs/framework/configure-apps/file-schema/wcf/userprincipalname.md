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
ms.openlocfilehash: 616eb07a76da93ff1019ea7e80b5ce3151e6e8a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="8e963-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="8e963-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="8e963-103">Určuje hlavní název uživatele (UPN) služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="8e963-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="8e963-104">Další informace o nastavení hlavního názvu uživatele najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8e963-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="8e963-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="8e963-105">\<identity></span></span>  
<span data-ttu-id="8e963-106">\<userPrincipalName ></span><span class="sxs-lookup"><span data-stu-id="8e963-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e963-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e963-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e963-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8e963-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8e963-109">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8e963-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e963-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8e963-110">Attributes</span></span>  
  
|<span data-ttu-id="8e963-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8e963-111">Attribute</span></span>|<span data-ttu-id="8e963-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8e963-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e963-113">value</span><span class="sxs-lookup"><span data-stu-id="8e963-113">value</span></span>|<span data-ttu-id="8e963-114">Název uživatelského účtu (někdy označované jako přihlašovací jméno uživatele) a název domény určujícího doménu, ve kterém se nachází uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="8e963-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="8e963-115">Toto je standardní použití pro přihlášení k doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8e963-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="8e963-116">Formát je: someone@example.com (jako u e-mailové adresy).</span><span class="sxs-lookup"><span data-stu-id="8e963-116">The format is: someone@example.com (as for an e-mail address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e963-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8e963-117">Child Elements</span></span>  
 <span data-ttu-id="8e963-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="8e963-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e963-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8e963-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8e963-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="8e963-120">Element</span></span>|<span data-ttu-id="8e963-121">Popis</span><span class="sxs-lookup"><span data-stu-id="8e963-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e963-122">\<identity ></span><span class="sxs-lookup"><span data-stu-id="8e963-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="8e963-123">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="8e963-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e963-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e963-124">Remarks</span></span>  
 <span data-ttu-id="8e963-125">Zabezpečený [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klienta, která se připojuje k koncový bod s tuto identitu používá název UPN při ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="8e963-125">A secure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e963-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e963-126">Example</span></span>  
 <span data-ttu-id="8e963-127">Následující kód konfigurace určuje UPN služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="8e963-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e963-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e963-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="8e963-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="8e963-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="8e963-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="8e963-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
