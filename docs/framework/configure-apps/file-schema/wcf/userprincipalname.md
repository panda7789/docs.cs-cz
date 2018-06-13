---
title: '&lt;userPrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 1bb0c8ac4cbe11cdfa31beb16b00b3863acabf92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358674"
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="647e0-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="647e0-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="647e0-103">Určuje hlavní název uživatele (UPN) služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="647e0-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="647e0-104">Další informace o nastavení hlavního názvu uživatele najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="647e0-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="647e0-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="647e0-105">\<identity></span></span>  
<span data-ttu-id="647e0-106">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="647e0-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="647e0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="647e0-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="647e0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="647e0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="647e0-109">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="647e0-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="647e0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="647e0-110">Attributes</span></span>  
  
|<span data-ttu-id="647e0-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="647e0-111">Attribute</span></span>|<span data-ttu-id="647e0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="647e0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="647e0-113">value</span><span class="sxs-lookup"><span data-stu-id="647e0-113">value</span></span>|<span data-ttu-id="647e0-114">Název uživatelského účtu (někdy označované jako přihlašovací jméno uživatele) a název domény určujícího doménu, ve kterém se nachází uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="647e0-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="647e0-115">Toto je standardní použití pro přihlášení k doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="647e0-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="647e0-116">Formát je: someone@example.com (jako u e-mailovou adresu).</span><span class="sxs-lookup"><span data-stu-id="647e0-116">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="647e0-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="647e0-117">Child Elements</span></span>  
 <span data-ttu-id="647e0-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="647e0-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="647e0-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="647e0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="647e0-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="647e0-120">Element</span></span>|<span data-ttu-id="647e0-121">Popis</span><span class="sxs-lookup"><span data-stu-id="647e0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="647e0-122">\<identity ></span><span class="sxs-lookup"><span data-stu-id="647e0-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="647e0-123">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="647e0-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="647e0-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="647e0-124">Remarks</span></span>  
 <span data-ttu-id="647e0-125">Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tuto identitu používá název UPN při ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="647e0-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="647e0-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="647e0-126">Example</span></span>  
 <span data-ttu-id="647e0-127">Následující kód konfigurace určuje UPN služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="647e0-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="647e0-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="647e0-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="647e0-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="647e0-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="647e0-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="647e0-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
