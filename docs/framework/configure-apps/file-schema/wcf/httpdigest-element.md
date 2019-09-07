---
title: Element <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: f392ebf4eeb6a008952fd4d5ef4e301e57f6eb31
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397996"
---
# <a name="httpdigest-element"></a><span data-ttu-id="62ab5-102">\<httpDigest – element ></span><span class="sxs-lookup"><span data-stu-id="62ab5-102">\<httpDigest> Element</span></span>
<span data-ttu-id="62ab5-103">Určuje typ Digest, který se použije při ověřování klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="62ab5-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
<span data-ttu-id="62ab5-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62ab5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62ab5-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="62ab5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="62ab5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62ab5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="62ab5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62ab5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="62ab5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="62ab5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="62ab5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="62ab5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="62ab5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpDigest >**</span><span class="sxs-lookup"><span data-stu-id="62ab5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62ab5-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62ab5-111">Syntax</span></span>  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62ab5-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="62ab5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="62ab5-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="62ab5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62ab5-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="62ab5-114">Attributes</span></span>  
  
|<span data-ttu-id="62ab5-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="62ab5-115">Attribute</span></span>|<span data-ttu-id="62ab5-116">Popis</span><span class="sxs-lookup"><span data-stu-id="62ab5-116">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="62ab5-117">Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="62ab5-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="62ab5-118">Režim zosobnění, který klient vybere, není na serveru vynutil.</span><span class="sxs-lookup"><span data-stu-id="62ab5-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="62ab5-119">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="62ab5-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62ab5-120">Identifikace Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="62ab5-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="62ab5-121">Zosobnění Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="62ab5-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="62ab5-122">Delegování Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="62ab5-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="62ab5-123">Anonymous Server nemůže zosobnit nebo identifikovat klienta.</span><span class="sxs-lookup"><span data-stu-id="62ab5-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="62ab5-124">NTato Úroveň zosobnění není přiřazena.</span><span class="sxs-lookup"><span data-stu-id="62ab5-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="62ab5-125">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="62ab5-125">The default is Identification.</span></span> <span data-ttu-id="62ab5-126">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="62ab5-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62ab5-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="62ab5-127">Child Elements</span></span>  
 <span data-ttu-id="62ab5-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="62ab5-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62ab5-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="62ab5-129">Parent Elements</span></span>  
  
|<span data-ttu-id="62ab5-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="62ab5-130">Element</span></span>|<span data-ttu-id="62ab5-131">Popis</span><span class="sxs-lookup"><span data-stu-id="62ab5-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62ab5-132">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="62ab5-132">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="62ab5-133">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="62ab5-133">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62ab5-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62ab5-134">Remarks</span></span>  
 <span data-ttu-id="62ab5-135">Výtah je hodnota hash určená pomocí algoritmu a sady vstupů.</span><span class="sxs-lookup"><span data-stu-id="62ab5-135">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="62ab5-136">Ověřovatel a ověřené souhlas s algoritmem a vyměňují data použitá jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="62ab5-136">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="62ab5-137">Klient může vypočítat hodnotu hash a odeslat ji do služby.</span><span class="sxs-lookup"><span data-stu-id="62ab5-137">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="62ab5-138">Služba také vypočítá hodnotu hash a porovná hodnoty.</span><span class="sxs-lookup"><span data-stu-id="62ab5-138">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="62ab5-139">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="62ab5-139">A match validates the client.</span></span>  
  
 <span data-ttu-id="62ab5-140">Tato funkce musí být povolená se službou Active Directory ve Windows a Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="62ab5-140">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="62ab5-141">Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="62ab5-141">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62ab5-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62ab5-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="62ab5-143">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="62ab5-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="62ab5-144">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="62ab5-144">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="62ab5-145">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="62ab5-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="62ab5-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="62ab5-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
