---
title: Element <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 914711e4d6c3dbb1ccc741af1b3abd6b8de716a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751043"
---
# <a name="httpdigest-element"></a><span data-ttu-id="173b9-102">\<httpDigest> Element</span><span class="sxs-lookup"><span data-stu-id="173b9-102">\<httpDigest> Element</span></span>
<span data-ttu-id="173b9-103">Určuje výběru pověření používaný při ověřování klienta ke službě zadejte.</span><span class="sxs-lookup"><span data-stu-id="173b9-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="173b9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="173b9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="173b9-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="173b9-105">\<behaviors></span></span>  
<span data-ttu-id="173b9-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="173b9-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="173b9-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="173b9-107">\<behavior></span></span>  
<span data-ttu-id="173b9-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="173b9-108">\<clientCredentials></span></span>  
<span data-ttu-id="173b9-109">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="173b9-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="173b9-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="173b9-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="173b9-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="173b9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="173b9-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="173b9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="173b9-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="173b9-113">Attributes</span></span>  
  
|<span data-ttu-id="173b9-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="173b9-114">Attribute</span></span>|<span data-ttu-id="173b9-115">Popis</span><span class="sxs-lookup"><span data-stu-id="173b9-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="173b9-116">Nastavuje předvolbu zosobnění, který klient komunikuje na server.</span><span class="sxs-lookup"><span data-stu-id="173b9-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="173b9-117">Režim zosobnění, který klient vybere nevynucuje na serveru.</span><span class="sxs-lookup"><span data-stu-id="173b9-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="173b9-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="173b9-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="173b9-119">-Identifikace: Na serveru můžete získat identit a oprávnění klienta, ale nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="173b9-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="173b9-120">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="173b9-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="173b9-121">-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="173b9-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="173b9-122">-Anonymní: Server nelze zosobnit nebo identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="173b9-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="173b9-123">-Žádný: Úroveň zosobnění není přiřazen.</span><span class="sxs-lookup"><span data-stu-id="173b9-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="173b9-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="173b9-124">The default is Identification.</span></span> <span data-ttu-id="173b9-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="173b9-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="173b9-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="173b9-126">Child Elements</span></span>  
 <span data-ttu-id="173b9-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="173b9-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="173b9-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="173b9-128">Parent Elements</span></span>  
  
|<span data-ttu-id="173b9-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="173b9-129">Element</span></span>|<span data-ttu-id="173b9-130">Popis</span><span class="sxs-lookup"><span data-stu-id="173b9-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="173b9-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="173b9-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="173b9-132">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="173b9-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="173b9-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="173b9-133">Remarks</span></span>  
 <span data-ttu-id="173b9-134">Přehled je hodnota hash určit pomocí algoritmu a sadu vstupů.</span><span class="sxs-lookup"><span data-stu-id="173b9-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="173b9-135">Ověřovacích a ověřeného odsouhlaste algoritmus a výměnu dat použít jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="173b9-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="173b9-136">Klient může vypočítat hodnotu hash a odesílat do služby.</span><span class="sxs-lookup"><span data-stu-id="173b9-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="173b9-137">Služba také vypočítá hodnotu hash a porovnává hodnoty.</span><span class="sxs-lookup"><span data-stu-id="173b9-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="173b9-138">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="173b9-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="173b9-139">Musí být povolena tato funkce se službou Active Directory na Windows a Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="173b9-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="173b9-140">Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="173b9-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="173b9-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="173b9-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="173b9-142">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="173b9-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="173b9-143">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="173b9-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="173b9-144">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="173b9-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="173b9-145">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="173b9-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
