---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 19ea7e940fc7013fc526629a8aac4361ff3fb8bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275013"
---
# <a name="userprincipalname"></a><span data-ttu-id="01f4b-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="01f4b-101">\<userPrincipalName></span></span>
<span data-ttu-id="01f4b-102">Určuje, hlavní název uživatele (UPN) služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="01f4b-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="01f4b-103">Další informace o nastavení hlavního názvu uživatele najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="01f4b-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="01f4b-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="01f4b-104">\<identity></span></span>  
<span data-ttu-id="01f4b-105">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="01f4b-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f4b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01f4b-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01f4b-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="01f4b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="01f4b-108">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="01f4b-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01f4b-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="01f4b-109">Attributes</span></span>  
  
|<span data-ttu-id="01f4b-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="01f4b-110">Attribute</span></span>|<span data-ttu-id="01f4b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="01f4b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01f4b-112">value</span><span class="sxs-lookup"><span data-stu-id="01f4b-112">value</span></span>|<span data-ttu-id="01f4b-113">Název uživatelského účtu (někdy označované jako přihlašovací uživatelské jméno) a název domény identifikující doménu, ve kterém se nachází uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="01f4b-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="01f4b-114">Toto je standardní využití pro přihlášení k doméně Windows.</span><span class="sxs-lookup"><span data-stu-id="01f4b-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="01f4b-115">Formát je: someone@example.com (jako u e-mailovou adresu).</span><span class="sxs-lookup"><span data-stu-id="01f4b-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01f4b-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="01f4b-116">Child Elements</span></span>  
 <span data-ttu-id="01f4b-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="01f4b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01f4b-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="01f4b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="01f4b-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="01f4b-119">Element</span></span>|<span data-ttu-id="01f4b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="01f4b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01f4b-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="01f4b-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="01f4b-122">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="01f4b-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01f4b-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01f4b-123">Remarks</span></span>  
 <span data-ttu-id="01f4b-124">Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tato identita se používá název UPN při provádění ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="01f4b-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01f4b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="01f4b-125">Example</span></span>  
 <span data-ttu-id="01f4b-126">Následující kód konfigurace určuje UPN služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="01f4b-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="01f4b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01f4b-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="01f4b-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="01f4b-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="01f4b-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="01f4b-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
