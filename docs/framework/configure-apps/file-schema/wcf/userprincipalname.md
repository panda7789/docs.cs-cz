---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 299af8c4a013d17d7c5b7285f6fb89892c4164a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854824"
---
# \<userPrincipalName>
<span data-ttu-id="4cc22-101">Určuje hlavní název uživatele (UPN) služby, který má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="4cc22-101">Specifies the User Principal Name (UPN) of a service to be authenticated by the client.</span></span>  
  
<span data-ttu-id="4cc22-102">Další informace o nastavení hlavního názvu uživatele (UPN) najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4cc22-102">For more information about setting the UPN, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userPrincipalName>**  
  
## <a name="syntax"></a><span data-ttu-id="4cc22-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cc22-103">Syntax</span></span>  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cc22-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4cc22-104">Attributes and Elements</span></span>  
 <span data-ttu-id="4cc22-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4cc22-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cc22-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="4cc22-106">Attributes</span></span>  
  
|<span data-ttu-id="4cc22-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="4cc22-107">Attribute</span></span>|<span data-ttu-id="4cc22-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4cc22-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4cc22-109">hodnota</span><span class="sxs-lookup"><span data-stu-id="4cc22-109">value</span></span>|<span data-ttu-id="4cc22-110">Název uživatelského účtu (někdy označovaný jako přihlašovací jméno uživatele) a název domény identifikující doménu, ve které se uživatelský účet nachází.</span><span class="sxs-lookup"><span data-stu-id="4cc22-110">A user account name (sometimes referred to as the user logon name) and a domain name identifying the domain in which the user account is located.</span></span> <span data-ttu-id="4cc22-111">Toto je standardní použití pro přihlášení k doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4cc22-111">This is the standard usage for logging on to a Windows domain.</span></span> <span data-ttu-id="4cc22-112">Formát je následující: someone@example.com (jako pro e-mailovou adresu).</span><span class="sxs-lookup"><span data-stu-id="4cc22-112">The format is: someone@example.com (as for an email address).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cc22-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4cc22-113">Child Elements</span></span>  
 <span data-ttu-id="4cc22-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="4cc22-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4cc22-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4cc22-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4cc22-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="4cc22-116">Element</span></span>|<span data-ttu-id="4cc22-117">Description</span><span class="sxs-lookup"><span data-stu-id="4cc22-117">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="4cc22-118">Určuje identitu služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="4cc22-118">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4cc22-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cc22-119">Remarks</span></span>  
 <span data-ttu-id="4cc22-120">Klient zabezpečeného Windows Communication Foundation (WCF), který se připojuje ke koncovému bodu s touto identitou, používá hlavní název uživatele (UPN) při provádění ověřování SSPI s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="4cc22-120">A secure Windows Communication Foundation (WCF) client that connects to an endpoint with this identity uses the UPN when performing SSPI authentication with the endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cc22-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="4cc22-121">Example</span></span>  
 <span data-ttu-id="4cc22-122">Následující konfigurační kód určuje hlavní název uživatele (UPN) služby, kterou má klient ověřit.</span><span class="sxs-lookup"><span data-stu-id="4cc22-122">The following configuration code specifies the UPN of the service to be authenticated by the client.</span></span>  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="4cc22-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="4cc22-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [<span data-ttu-id="4cc22-124">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="4cc22-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
