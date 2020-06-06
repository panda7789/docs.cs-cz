---
title: Element <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 328411a429cd42927a190c6805a1f5e2b3555ea1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448449"
---
# <a name="httpdigest-element"></a><span data-ttu-id="b6efb-102">Element \<httpDigest></span><span class="sxs-lookup"><span data-stu-id="b6efb-102">\<httpDigest> Element</span></span>
<span data-ttu-id="b6efb-103">Určuje typ Digest, který se použije při ověřování klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="b6efb-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**  
  
## <a name="syntax"></a><span data-ttu-id="b6efb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6efb-104">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6efb-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b6efb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b6efb-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b6efb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6efb-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b6efb-107">Attributes</span></span>  
  
|<span data-ttu-id="b6efb-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b6efb-108">Attribute</span></span>|<span data-ttu-id="b6efb-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b6efb-109">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="b6efb-110">Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="b6efb-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="b6efb-111">Režim zosobnění, který klient vybere, není na serveru vynutil.</span><span class="sxs-lookup"><span data-stu-id="b6efb-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="b6efb-112">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="b6efb-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b6efb-113">-Identifikace: Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="b6efb-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="b6efb-114">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="b6efb-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="b6efb-115">-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="b6efb-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="b6efb-116">-Anonymní: Server nemůže zosobnit nebo identifikovat klienta.</span><span class="sxs-lookup"><span data-stu-id="b6efb-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="b6efb-117">-None: úroveň zosobnění není přiřazena.</span><span class="sxs-lookup"><span data-stu-id="b6efb-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="b6efb-118">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="b6efb-118">The default is Identification.</span></span> <span data-ttu-id="b6efb-119">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="b6efb-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6efb-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b6efb-120">Child Elements</span></span>  
 <span data-ttu-id="b6efb-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="b6efb-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6efb-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b6efb-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b6efb-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6efb-123">Element</span></span>|<span data-ttu-id="b6efb-124">Description</span><span class="sxs-lookup"><span data-stu-id="b6efb-124">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="b6efb-125">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="b6efb-125">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6efb-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6efb-126">Remarks</span></span>  
 <span data-ttu-id="b6efb-127">Výtah je hodnota hash určená pomocí algoritmu a sady vstupů.</span><span class="sxs-lookup"><span data-stu-id="b6efb-127">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="b6efb-128">Ověřovatel a ověřené souhlas s algoritmem a vyměňují data použitá jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="b6efb-128">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="b6efb-129">Klient může vypočítat hodnotu hash a odeslat ji do služby.</span><span class="sxs-lookup"><span data-stu-id="b6efb-129">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="b6efb-130">Služba také vypočítá hodnotu hash a porovná hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b6efb-130">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="b6efb-131">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="b6efb-131">A match validates the client.</span></span>  
  
 <span data-ttu-id="b6efb-132">Tato funkce musí být povolená se službou Active Directory ve Windows a Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="b6efb-132">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="b6efb-133">Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="b6efb-133">For more information, see [Digest Authentication in IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6efb-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6efb-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="b6efb-135">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b6efb-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b6efb-136">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="b6efb-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b6efb-137">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="b6efb-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b6efb-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b6efb-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
