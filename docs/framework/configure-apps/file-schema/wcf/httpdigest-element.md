---
title: Element <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 2ceefdd7fab82025e89ad08d8423d57524c2e4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925561"
---
# <a name="httpdigest-element"></a><span data-ttu-id="84019-102">\<httpDigest – element ></span><span class="sxs-lookup"><span data-stu-id="84019-102">\<httpDigest> Element</span></span>
<span data-ttu-id="84019-103">Určuje typ Digest, který se použije při ověřování klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="84019-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="84019-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="84019-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="84019-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="84019-105">\<behaviors></span></span>  
<span data-ttu-id="84019-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="84019-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="84019-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="84019-107">\<behavior></span></span>  
<span data-ttu-id="84019-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="84019-108">\<clientCredentials></span></span>  
<span data-ttu-id="84019-109">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="84019-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84019-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84019-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84019-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="84019-111">Attributes and Elements</span></span>  
 <span data-ttu-id="84019-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="84019-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84019-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="84019-113">Attributes</span></span>  
  
|<span data-ttu-id="84019-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="84019-114">Attribute</span></span>|<span data-ttu-id="84019-115">Popis</span><span class="sxs-lookup"><span data-stu-id="84019-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="84019-116">Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="84019-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="84019-117">Režim zosobnění, který klient vybere, není na serveru vynutil.</span><span class="sxs-lookup"><span data-stu-id="84019-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="84019-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="84019-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="84019-119">Identifikace Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="84019-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="84019-120">Zosobnění Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="84019-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="84019-121">Delegování Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="84019-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="84019-122">Anonymous Server nemůže zosobnit nebo identifikovat klienta.</span><span class="sxs-lookup"><span data-stu-id="84019-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="84019-123">NTato Úroveň zosobnění není přiřazena.</span><span class="sxs-lookup"><span data-stu-id="84019-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="84019-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="84019-124">The default is Identification.</span></span> <span data-ttu-id="84019-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="84019-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84019-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="84019-126">Child Elements</span></span>  
 <span data-ttu-id="84019-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="84019-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84019-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="84019-128">Parent Elements</span></span>  
  
|<span data-ttu-id="84019-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="84019-129">Element</span></span>|<span data-ttu-id="84019-130">Popis</span><span class="sxs-lookup"><span data-stu-id="84019-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84019-131">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="84019-131">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="84019-132">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="84019-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84019-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84019-133">Remarks</span></span>  
 <span data-ttu-id="84019-134">Výtah je hodnota hash určená pomocí algoritmu a sady vstupů.</span><span class="sxs-lookup"><span data-stu-id="84019-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="84019-135">Ověřovatel a ověřené souhlas s algoritmem a vyměňují data použitá jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="84019-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="84019-136">Klient může vypočítat hodnotu hash a odeslat ji do služby.</span><span class="sxs-lookup"><span data-stu-id="84019-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="84019-137">Služba také vypočítá hodnotu hash a porovná hodnoty.</span><span class="sxs-lookup"><span data-stu-id="84019-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="84019-138">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="84019-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="84019-139">Tato funkce musí být povolená se službou Active Directory ve Windows a Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="84019-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="84019-140">Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="84019-140">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84019-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84019-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="84019-142">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="84019-142">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="84019-143">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="84019-143">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="84019-144">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="84019-144">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="84019-145">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="84019-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
