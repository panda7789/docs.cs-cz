---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 423a3249a9298675517f0cff08566c3735fa35f1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940514"
---
# <a name="userprincipalname"></a><span data-ttu-id="df817-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="df817-101">\<userPrincipalName></span></span>
<span data-ttu-id="df817-102">Určuje hlavní název uživatele (UPN) služby, který má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="df817-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
 <span data-ttu-id="df817-103">Další informace o nastavení hlavního názvu uživatele (UPN) najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="df817-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="df817-104">\<> identity</span><span class="sxs-lookup"><span data-stu-id="df817-104">\<identity></span></span>  
<span data-ttu-id="df817-105">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="df817-105">\<userPrincipalName></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df817-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df817-106">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df817-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="df817-107">Attributes and Elements</span></span>  
 <span data-ttu-id="df817-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="df817-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df817-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="df817-109">Attributes</span></span>  
  
|<span data-ttu-id="df817-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="df817-110">Attribute</span></span>|<span data-ttu-id="df817-111">Popis</span><span class="sxs-lookup"><span data-stu-id="df817-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df817-112">value</span><span class="sxs-lookup"><span data-stu-id="df817-112">value</span></span>|<span data-ttu-id="df817-113">Název uživatelského účtu (někdy označovaný jako přihlašovací jméno uživatele) a název domény identifikující doménu, ve které se uživatelský účet nachází.</span><span class="sxs-lookup"><span data-stu-id="df817-113">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="df817-114">Toto je standardní použití pro přihlášení k doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="df817-114">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="df817-115">Formát je následující: someone@example.com (jako pro e-mailovou adresu).</span><span class="sxs-lookup"><span data-stu-id="df817-115">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df817-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="df817-116">Child Elements</span></span>  
 <span data-ttu-id="df817-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="df817-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df817-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="df817-118">Parent Elements</span></span>  
  
|<span data-ttu-id="df817-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="df817-119">Element</span></span>|<span data-ttu-id="df817-120">Popis</span><span class="sxs-lookup"><span data-stu-id="df817-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df817-121">\<identity></span><span class="sxs-lookup"><span data-stu-id="df817-121">\<identity></span></span>](identity.md)|<span data-ttu-id="df817-122">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="df817-122">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df817-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df817-123">Remarks</span></span>  
 <span data-ttu-id="df817-124">Klient zabezpečeného Windows Communication Foundation (WCF), který se připojuje ke koncovému bodu s touto identitou, používá hlavní název uživatele (UPN) při provádění ověřování SSPI s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="df817-124">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df817-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="df817-125">Example</span></span>  
 <span data-ttu-id="df817-126">Následující konfigurační kód určuje hlavní název uživatele (UPN) služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="df817-126">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="df817-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df817-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="df817-128">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="df817-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="df817-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="df817-129">\<identity></span></span>](identity.md)
