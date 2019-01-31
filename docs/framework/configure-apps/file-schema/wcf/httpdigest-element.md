---
title: Element <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: c930efbc2cd7a6dc12795d5ac1c26ea92fc36599
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259004"
---
# <a name="httpdigest-element"></a><span data-ttu-id="a409a-102">\<httpDigest> Element</span><span class="sxs-lookup"><span data-stu-id="a409a-102">\<httpDigest> Element</span></span>
<span data-ttu-id="a409a-103">Určuje výběru pověření používaný při ověřování klienta ke službě zadejte.</span><span class="sxs-lookup"><span data-stu-id="a409a-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="a409a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a409a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a409a-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a409a-105">\<behaviors></span></span>  
<span data-ttu-id="a409a-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a409a-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="a409a-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="a409a-107">\<behavior></span></span>  
<span data-ttu-id="a409a-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a409a-108">\<clientCredentials></span></span>  
<span data-ttu-id="a409a-109">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="a409a-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a409a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a409a-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a409a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a409a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a409a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a409a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a409a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a409a-113">Attributes</span></span>  
  
|<span data-ttu-id="a409a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a409a-114">Attribute</span></span>|<span data-ttu-id="a409a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a409a-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="a409a-116">Nastavuje předvolbu zosobnění, který klient komunikuje na server.</span><span class="sxs-lookup"><span data-stu-id="a409a-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="a409a-117">Režim zosobnění, který klient vybere nevynucuje na serveru.</span><span class="sxs-lookup"><span data-stu-id="a409a-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="a409a-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="a409a-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a409a-119">-Identifikace: Na serveru můžete získat identit a oprávnění klienta, ale nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="a409a-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="a409a-120">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="a409a-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="a409a-121">-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="a409a-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="a409a-122">-Anonymní: Server nelze zosobnit nebo identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="a409a-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="a409a-123">-Žádný: Úroveň zosobnění není přiřazen.</span><span class="sxs-lookup"><span data-stu-id="a409a-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="a409a-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="a409a-124">The default is Identification.</span></span> <span data-ttu-id="a409a-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="a409a-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a409a-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a409a-126">Child Elements</span></span>  
 <span data-ttu-id="a409a-127">Žádná</span><span class="sxs-lookup"><span data-stu-id="a409a-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a409a-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a409a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a409a-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="a409a-129">Element</span></span>|<span data-ttu-id="a409a-130">Popis</span><span class="sxs-lookup"><span data-stu-id="a409a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a409a-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a409a-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="a409a-132">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="a409a-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a409a-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a409a-133">Remarks</span></span>  
 <span data-ttu-id="a409a-134">Přehled je hodnota hash určit pomocí algoritmu a sadu vstupů.</span><span class="sxs-lookup"><span data-stu-id="a409a-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="a409a-135">Ověřovacích a ověřeného odsouhlaste algoritmus a výměnu dat použít jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="a409a-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="a409a-136">Klient může vypočítat hodnotu hash a odesílat do služby.</span><span class="sxs-lookup"><span data-stu-id="a409a-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="a409a-137">Služba také vypočítá hodnotu hash a porovnává hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a409a-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="a409a-138">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="a409a-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="a409a-139">Musí být povolena tato funkce se službou Active Directory na Windows a Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="a409a-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="a409a-140">Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="a409a-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a409a-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a409a-141">See also</span></span>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="a409a-142">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a409a-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a409a-143">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="a409a-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="a409a-144">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="a409a-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a409a-145">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a409a-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
