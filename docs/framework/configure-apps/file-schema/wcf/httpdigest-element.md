---
title: Element &lt;httpDigest&gt;
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 75579a583b774896f43099d3cc30f1679b10a889
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="lthttpdigestgt-element"></a><span data-ttu-id="d6362-102">Element &lt;httpDigest&gt;</span><span class="sxs-lookup"><span data-stu-id="d6362-102">&lt;httpDigest&gt; Element</span></span>
<span data-ttu-id="d6362-103">Určuje výtah zadejte pověření používaná při ověřování klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="d6362-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="d6362-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d6362-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d6362-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d6362-105">\<behaviors></span></span>  
<span data-ttu-id="d6362-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d6362-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d6362-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d6362-107">\<behavior></span></span>  
<span data-ttu-id="d6362-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d6362-108">\<clientCredentials></span></span>  
<span data-ttu-id="d6362-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="d6362-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6362-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6362-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6362-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6362-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6362-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6362-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6362-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6362-113">Attributes</span></span>  
  
|<span data-ttu-id="d6362-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d6362-114">Attribute</span></span>|<span data-ttu-id="d6362-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d6362-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="d6362-116">Nastaví zosobnění předvoleb, které klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="d6362-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="d6362-117">Režim zosobnění, který klient vybere nevynucuje na serveru.</span><span class="sxs-lookup"><span data-stu-id="d6362-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="d6362-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="d6362-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d6362-119">-Identifikace: Na serveru můžete získat identitu a oprávnění klienta, ale nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="d6362-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="d6362-120">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="d6362-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="d6362-121">-Delegování: Server může zosobnit kontext zabezpečení klienta na vzdálené systémy.</span><span class="sxs-lookup"><span data-stu-id="d6362-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="d6362-122">-Anonymní: Server nelze zosobnit nebo identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="d6362-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="d6362-123">-None: Není přiřazen úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="d6362-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="d6362-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="d6362-124">The default is Identification.</span></span> <span data-ttu-id="d6362-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="d6362-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6362-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6362-126">Child Elements</span></span>  
 <span data-ttu-id="d6362-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="d6362-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6362-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6362-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d6362-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6362-129">Element</span></span>|<span data-ttu-id="d6362-130">Popis</span><span class="sxs-lookup"><span data-stu-id="d6362-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6362-131">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d6362-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="d6362-132">Určuje pověření použitá k ověření klienta pro službu.</span><span class="sxs-lookup"><span data-stu-id="d6362-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6362-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6362-133">Remarks</span></span>  
 <span data-ttu-id="d6362-134">Algoritmu digest je hodnota hash určit pomocí algoritmu a sadu vstupy.</span><span class="sxs-lookup"><span data-stu-id="d6362-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="d6362-135">Ověřovatele a ověřený odsouhlaste algoritmu a výměnu dat použít jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="d6362-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="d6362-136">Klienta můžete vypočítat hodnotu hash a odeslat do služby.</span><span class="sxs-lookup"><span data-stu-id="d6362-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="d6362-137">Služba také vypočte hash a porovnává hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d6362-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="d6362-138">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="d6362-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="d6362-139">Musí být povolena tato funkce se službou Active Directory ve Windows a Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="d6362-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="d6362-140">Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="d6362-140">For more information, see [Digest Authentication in IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6362-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6362-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [<span data-ttu-id="d6362-142">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d6362-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="d6362-143">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="d6362-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="d6362-144">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="d6362-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="d6362-145">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d6362-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
