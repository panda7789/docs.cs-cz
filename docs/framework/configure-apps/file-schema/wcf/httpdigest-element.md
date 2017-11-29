---
title: Element &lt;httpDigest&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22c89aa69ea686274bb232eb04eec930ffc5b51d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lthttpdigestgt-element"></a><span data-ttu-id="5b445-102">Element &lt;httpDigest&gt;</span><span class="sxs-lookup"><span data-stu-id="5b445-102">&lt;httpDigest&gt; Element</span></span>
<span data-ttu-id="5b445-103">Určuje výtah zadejte pověření používaná při ověřování klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="5b445-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
 <span data-ttu-id="5b445-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5b445-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5b445-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5b445-105">\<behaviors></span></span>  
<span data-ttu-id="5b445-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5b445-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5b445-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5b445-107">\<behavior></span></span>  
<span data-ttu-id="5b445-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5b445-108">\<clientCredentials></span></span>  
<span data-ttu-id="5b445-109">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="5b445-109">\<httpDigest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b445-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b445-110">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b445-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5b445-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5b445-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5b445-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b445-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5b445-113">Attributes</span></span>  
  
|<span data-ttu-id="5b445-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="5b445-114">Attribute</span></span>|<span data-ttu-id="5b445-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5b445-115">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="5b445-116">Nastaví zosobnění předvoleb, které klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="5b445-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="5b445-117">Režim zosobnění, který klient vybere nevynucuje na serveru.</span><span class="sxs-lookup"><span data-stu-id="5b445-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="5b445-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="5b445-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5b445-119">-Identifikace: Na serveru můžete získat identitu a oprávnění klienta, ale nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="5b445-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="5b445-120">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="5b445-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="5b445-121">-Delegování: Server může zosobnit kontext zabezpečení klienta na vzdálené systémy.</span><span class="sxs-lookup"><span data-stu-id="5b445-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="5b445-122">-Anonymní: Server nelze zosobnit nebo identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="5b445-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="5b445-123">-None: Není přiřazen úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="5b445-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="5b445-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="5b445-124">The default is Identification.</span></span> <span data-ttu-id="5b445-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="5b445-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b445-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5b445-126">Child Elements</span></span>  
 <span data-ttu-id="5b445-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="5b445-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b445-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5b445-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5b445-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="5b445-129">Element</span></span>|<span data-ttu-id="5b445-130">Popis</span><span class="sxs-lookup"><span data-stu-id="5b445-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b445-131">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5b445-131">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="5b445-132">Určuje pověření použitá k ověření klienta pro službu.</span><span class="sxs-lookup"><span data-stu-id="5b445-132">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b445-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b445-133">Remarks</span></span>  
 <span data-ttu-id="5b445-134">Algoritmu digest je hodnota hash určit pomocí algoritmu a sadu vstupy.</span><span class="sxs-lookup"><span data-stu-id="5b445-134">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="5b445-135">Ověřovatele a ověřený odsouhlaste algoritmu a výměnu dat použít jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="5b445-135">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="5b445-136">Klienta můžete vypočítat hodnotu hash a odeslat do služby.</span><span class="sxs-lookup"><span data-stu-id="5b445-136">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="5b445-137">Služba také vypočte hash a porovnává hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5b445-137">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="5b445-138">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="5b445-138">A match validates the client.</span></span>  
  
 <span data-ttu-id="5b445-139">Musí být povolena tato funkce se službou Active Directory ve Windows a Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="5b445-139">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)]<span data-ttu-id="5b445-140">[Ve službě IIS 6.0 ověřování algoritmem digest](http://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="5b445-140"> [Digest Authentication in IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b445-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b445-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [<span data-ttu-id="5b445-142">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5b445-142">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="5b445-143">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="5b445-143">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="5b445-144">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="5b445-144">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="5b445-145">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5b445-145">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
