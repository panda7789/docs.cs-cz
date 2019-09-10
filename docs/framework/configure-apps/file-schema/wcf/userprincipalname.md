---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854824"
---
# <a name="userprincipalname"></a><span data-ttu-id="55781-101">\<userPrincipalName></span><span class="sxs-lookup"><span data-stu-id="55781-101">\<userPrincipalName></span></span>
<span data-ttu-id="55781-102">Určuje hlavní název uživatele (UPN) služby, který má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="55781-102">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="55781-103">Další informace o nastavení hlavního názvu uživatele (UPN) najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="55781-103">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="55781-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="55781-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="55781-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="55781-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="55781-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="55781-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="55781-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="55781-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="55781-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identity**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="55781-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="55781-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userPrincipalName – >**</span><span class="sxs-lookup"><span data-stu-id="55781-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55781-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55781-110">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55781-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="55781-111">Attributes and Elements</span></span>  
 <span data-ttu-id="55781-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="55781-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55781-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="55781-113">Attributes</span></span>  
  
|<span data-ttu-id="55781-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="55781-114">Attribute</span></span>|<span data-ttu-id="55781-115">Popis</span><span class="sxs-lookup"><span data-stu-id="55781-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55781-116">value</span><span class="sxs-lookup"><span data-stu-id="55781-116">value</span></span>|<span data-ttu-id="55781-117">Název uživatelského účtu (někdy označovaný jako přihlašovací jméno uživatele) a název domény identifikující doménu, ve které se uživatelský účet nachází.</span><span class="sxs-lookup"><span data-stu-id="55781-117">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="55781-118">Toto je standardní použití pro přihlášení k doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="55781-118">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="55781-119">Formát je následující: someone@example.com (jako pro e-mailovou adresu).</span><span class="sxs-lookup"><span data-stu-id="55781-119">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55781-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="55781-120">Child Elements</span></span>  
 <span data-ttu-id="55781-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="55781-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55781-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="55781-122">Parent Elements</span></span>  
  
|<span data-ttu-id="55781-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="55781-123">Element</span></span>|<span data-ttu-id="55781-124">Popis</span><span class="sxs-lookup"><span data-stu-id="55781-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55781-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="55781-125">\<identity></span></span>](identity.md)|<span data-ttu-id="55781-126">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="55781-126">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55781-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55781-127">Remarks</span></span>  
 <span data-ttu-id="55781-128">Klient zabezpečeného Windows Communication Foundation (WCF), který se připojuje ke koncovému bodu s touto identitou, používá hlavní název uživatele (UPN) při provádění ověřování SSPI s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="55781-128">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55781-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="55781-129">Example</span></span>  
 <span data-ttu-id="55781-130">Následující konfigurační kód určuje hlavní název uživatele (UPN) služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="55781-130">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="55781-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55781-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="55781-132">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="55781-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="55781-133">\<identity></span><span class="sxs-lookup"><span data-stu-id="55781-133">\<identity></span></span>](identity.md)
