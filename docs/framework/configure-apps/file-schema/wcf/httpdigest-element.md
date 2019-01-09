---
title: Element &lt;httpDigest&gt;
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2211c593090d697ae07350fcf7ac491b9d23e2d0
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150137"
---
# <a name="lthttpdigestgt-element"></a><span data-ttu-id="79a68-102">Element &lt;httpDigest&gt;</span><span class="sxs-lookup"><span data-stu-id="79a68-102">&lt;httpDigest&gt; Element</span></span>
<span data-ttu-id="79a68-103">Určuje výběru pověření používaný při ověřování klienta ke službě zadejte.</span><span class="sxs-lookup"><span data-stu-id="79a68-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="79a68-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="79a68-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="79a68-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="79a68-105">\<behaviors></span></span>  
<span data-ttu-id="79a68-106">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="79a68-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="79a68-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="79a68-107">\<behavior></span></span>  
<span data-ttu-id="79a68-108">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="79a68-108">\<clientCredentials></span></span>  
<span data-ttu-id="79a68-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="79a68-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79a68-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79a68-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79a68-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="79a68-111">Attributes and Elements</span></span>  
 <span data-ttu-id="79a68-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="79a68-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79a68-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="79a68-113">Attributes</span></span>  
  
|<span data-ttu-id="79a68-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="79a68-114">Attribute</span></span>|<span data-ttu-id="79a68-115">Popis</span><span class="sxs-lookup"><span data-stu-id="79a68-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="79a68-116">Nastavuje předvolbu zosobnění, který klient komunikuje na server.</span><span class="sxs-lookup"><span data-stu-id="79a68-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="79a68-117">Režim zosobnění, který klient vybere nevynucuje na serveru.</span><span class="sxs-lookup"><span data-stu-id="79a68-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="79a68-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="79a68-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="79a68-119">-Identifikace: Na serveru můžete získat identit a oprávnění klienta, ale nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="79a68-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="79a68-120">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="79a68-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="79a68-121">-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="79a68-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="79a68-122">-Anonymní: Server nelze zosobnit nebo identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="79a68-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="79a68-123">-Žádný: Úroveň zosobnění není přiřazen.</span><span class="sxs-lookup"><span data-stu-id="79a68-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="79a68-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="79a68-124">The default is Identification.</span></span> <span data-ttu-id="79a68-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="79a68-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79a68-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="79a68-126">Child Elements</span></span>  
 <span data-ttu-id="79a68-127">Žádná</span><span class="sxs-lookup"><span data-stu-id="79a68-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79a68-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="79a68-128">Parent Elements</span></span>  
  
|<span data-ttu-id="79a68-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="79a68-129">Element</span></span>|<span data-ttu-id="79a68-130">Popis</span><span class="sxs-lookup"><span data-stu-id="79a68-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="79a68-131">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="79a68-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="79a68-132">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="79a68-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79a68-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79a68-133">Remarks</span></span>  
 <span data-ttu-id="79a68-134">Přehled je hodnota hash určit pomocí algoritmu a sadu vstupů.</span><span class="sxs-lookup"><span data-stu-id="79a68-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="79a68-135">Ověřovacích a ověřeného odsouhlaste algoritmus a výměnu dat použít jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="79a68-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="79a68-136">Klient může vypočítat hodnotu hash a odesílat do služby.</span><span class="sxs-lookup"><span data-stu-id="79a68-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="79a68-137">Služba také vypočítá hodnotu hash a porovnává hodnoty.</span><span class="sxs-lookup"><span data-stu-id="79a68-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="79a68-138">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="79a68-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="79a68-139">Musí být povolena tato funkce se službou Active Directory na Windows a Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="79a68-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="79a68-140">Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="79a68-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a68-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="79a68-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [<span data-ttu-id="79a68-142">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="79a68-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="79a68-143">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="79a68-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="79a68-144">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="79a68-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="79a68-145">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="79a68-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
