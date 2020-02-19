---
title: Element <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 328411a429cd42927a190c6805a1f5e2b3555ea1
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448449"
---
# <a name="httpdigest-element"></a><span data-ttu-id="54986-102">\<element > httpDigest</span><span class="sxs-lookup"><span data-stu-id="54986-102">\<httpDigest> Element</span></span>
<span data-ttu-id="54986-103">Určuje typ Digest, který se použije při ověřování klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="54986-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
<span data-ttu-id="54986-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="54986-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="54986-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="54986-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="54986-106">&nbsp;&nbsp;&nbsp;&nbsp;[**chování**](behaviors.md)\<></span><span class="sxs-lookup"><span data-stu-id="54986-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="54986-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="54986-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="54986-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<chování**](behavior-of-endpointbehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="54986-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="54986-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="54986-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="54986-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpDigest >**</span><span class="sxs-lookup"><span data-stu-id="54986-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54986-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54986-111">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54986-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="54986-112">Attributes and Elements</span></span>  
 <span data-ttu-id="54986-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="54986-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54986-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="54986-114">Attributes</span></span>  
  
|<span data-ttu-id="54986-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="54986-115">Attribute</span></span>|<span data-ttu-id="54986-116">Popis</span><span class="sxs-lookup"><span data-stu-id="54986-116">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="54986-117">Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="54986-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="54986-118">Režim zosobnění, který klient vybere, není na serveru vynutil.</span><span class="sxs-lookup"><span data-stu-id="54986-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="54986-119">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="54986-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="54986-120">-Identifikace: Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="54986-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="54986-121">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="54986-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="54986-122">-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="54986-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="54986-123">-Anonymní: Server nemůže zosobnit nebo identifikovat klienta.</span><span class="sxs-lookup"><span data-stu-id="54986-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="54986-124">-None: úroveň zosobnění není přiřazena.</span><span class="sxs-lookup"><span data-stu-id="54986-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="54986-125">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="54986-125">The default is Identification.</span></span> <span data-ttu-id="54986-126">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="54986-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54986-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="54986-127">Child Elements</span></span>  
 <span data-ttu-id="54986-128">Žádná</span><span class="sxs-lookup"><span data-stu-id="54986-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54986-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="54986-129">Parent Elements</span></span>  
  
|<span data-ttu-id="54986-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="54986-130">Element</span></span>|<span data-ttu-id="54986-131">Popis</span><span class="sxs-lookup"><span data-stu-id="54986-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54986-132">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="54986-132">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="54986-133">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="54986-133">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54986-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54986-134">Remarks</span></span>  
 <span data-ttu-id="54986-135">Výtah je hodnota hash určená pomocí algoritmu a sady vstupů.</span><span class="sxs-lookup"><span data-stu-id="54986-135">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="54986-136">Ověřovatel a ověřené souhlas s algoritmem a vyměňují data použitá jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="54986-136">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="54986-137">Klient může vypočítat hodnotu hash a odeslat ji do služby.</span><span class="sxs-lookup"><span data-stu-id="54986-137">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="54986-138">Služba také vypočítá hodnotu hash a porovná hodnoty.</span><span class="sxs-lookup"><span data-stu-id="54986-138">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="54986-139">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="54986-139">A match validates the client.</span></span>  
  
 <span data-ttu-id="54986-140">Tato funkce musí být povolená se službou Active Directory ve Windows a Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="54986-140">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="54986-141">Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span><span class="sxs-lookup"><span data-stu-id="54986-141">For more information, see [Digest Authentication in IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54986-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="54986-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="54986-143">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="54986-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="54986-144">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="54986-144">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="54986-145">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="54986-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="54986-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="54986-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
