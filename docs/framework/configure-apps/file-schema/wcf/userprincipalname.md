---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 9e7b845d39495dba1d1a19af95faf308b8b8c0fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769808"
---
# <a name="userprincipalname"></a><span data-ttu-id="51d18-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="51d18-101">\<userPrincipalName></span></span>
<span data-ttu-id="51d18-102">Určuje, hlavní název uživatele (UPN) služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="51d18-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="51d18-103">Další informace o nastavení hlavního názvu uživatele najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="51d18-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="51d18-104">\<identity></span><span class="sxs-lookup"><span data-stu-id="51d18-104">\<identity></span></span>  
<span data-ttu-id="51d18-105">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="51d18-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51d18-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51d18-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51d18-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="51d18-107">Attributes and Elements</span></span>  
 <span data-ttu-id="51d18-108">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="51d18-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51d18-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="51d18-109">Attributes</span></span>  
  
|<span data-ttu-id="51d18-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="51d18-110">Attribute</span></span>|<span data-ttu-id="51d18-111">Popis</span><span class="sxs-lookup"><span data-stu-id="51d18-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="51d18-112">value</span><span class="sxs-lookup"><span data-stu-id="51d18-112">value</span></span>|<span data-ttu-id="51d18-113">Název uživatelského účtu (někdy označované jako přihlašovací uživatelské jméno) a název domény identifikující doménu, ve kterém se nachází uživatelský účet.</span><span class="sxs-lookup"><span data-stu-id="51d18-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="51d18-114">Toto je standardní využití pro přihlášení k doméně Windows.</span><span class="sxs-lookup"><span data-stu-id="51d18-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="51d18-115">Formát je: someone@example.com (jako u e-mailovou adresu).</span><span class="sxs-lookup"><span data-stu-id="51d18-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="51d18-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="51d18-116">Child Elements</span></span>  
 <span data-ttu-id="51d18-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="51d18-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="51d18-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="51d18-118">Parent Elements</span></span>  
  
|<span data-ttu-id="51d18-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="51d18-119">Element</span></span>|<span data-ttu-id="51d18-120">Popis</span><span class="sxs-lookup"><span data-stu-id="51d18-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51d18-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="51d18-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="51d18-122">Určuje identitu služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="51d18-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51d18-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="51d18-123">Remarks</span></span>  
 <span data-ttu-id="51d18-124">Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tato identita se používá název UPN při provádění ověřování rozhraní SSPI ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="51d18-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51d18-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="51d18-125">Example</span></span>  
 <span data-ttu-id="51d18-126">Následující kód konfigurace určuje UPN služby k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="51d18-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="51d18-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="51d18-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="51d18-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="51d18-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="51d18-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="51d18-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
