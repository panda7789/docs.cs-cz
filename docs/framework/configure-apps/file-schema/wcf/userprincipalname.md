---
title: '&lt;userPrincipalName&gt;'
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: ff38a6975d1ec73c1a3014b94198ba630c3fec31
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149977"
---
# <a name="ltuserprincipalnamegt"></a><span data-ttu-id="44a0e-102">&lt;userPrincipalName&gt;</span><span class="sxs-lookup"><span data-stu-id="44a0e-102">&lt;userPrincipalName&gt;</span></span>
<span data-ttu-id="44a0e-103">Určuje, hlavní název uživatele (UPN) služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="44a0e-103">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="44a0e-104">Další informace o nastavení hlavního názvu uživatele najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="44a0e-104">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="44a0e-105">\<identity ></span><span class="sxs-lookup"><span data-stu-id="44a0e-105">\<identity></span></span>  
<span data-ttu-id="44a0e-106">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="44a0e-106">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44a0e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44a0e-107">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44a0e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44a0e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="44a0e-109">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44a0e-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44a0e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="44a0e-110">Attributes</span></span>  
  
|<span data-ttu-id="44a0e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="44a0e-111">Attribute</span></span>|<span data-ttu-id="44a0e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="44a0e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44a0e-113">value</span><span class="sxs-lookup"><span data-stu-id="44a0e-113">value</span></span>|<span data-ttu-id="44a0e-114">Název uživatelského účtu (někdy označované jako přihlašovací uživatelské jméno) a název domény identifikující doménu, ve kterém se nachází uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="44a0e-114">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="44a0e-115">Toto je standardní využití pro přihlášení k doméně Windows.</span><span class="sxs-lookup"><span data-stu-id="44a0e-115">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="44a0e-116">Formát je: someone@example.com (jako u e-mailovou adresu).</span><span class="sxs-lookup"><span data-stu-id="44a0e-116">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44a0e-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="44a0e-117">Child Elements</span></span>  
 <span data-ttu-id="44a0e-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="44a0e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44a0e-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44a0e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="44a0e-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="44a0e-120">Element</span></span>|<span data-ttu-id="44a0e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="44a0e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44a0e-122">\<identity ></span><span class="sxs-lookup"><span data-stu-id="44a0e-122">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="44a0e-123">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="44a0e-123">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44a0e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44a0e-124">Remarks</span></span>  
 <span data-ttu-id="44a0e-125">Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tato identita se používá název UPN při provádění ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="44a0e-125">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44a0e-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="44a0e-126">Example</span></span>  
 <span data-ttu-id="44a0e-127">Následující kód konfigurace určuje UPN služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="44a0e-127">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="44a0e-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="44a0e-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [<span data-ttu-id="44a0e-129">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="44a0e-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="44a0e-130">\<identity ></span><span class="sxs-lookup"><span data-stu-id="44a0e-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
