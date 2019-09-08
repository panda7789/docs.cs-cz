---
title: Element <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 121df39c7e4ce4de5c1f0ef87921f6269d7cc1c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785823"
---
# <a name="httpdigest-element"></a><span data-ttu-id="64208-102">\<httpDigest – element ></span><span class="sxs-lookup"><span data-stu-id="64208-102">\<httpDigest> Element</span></span>
<span data-ttu-id="64208-103">Určuje typ Digest, který se použije při ověřování klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="64208-103">Specifies a digest type credential used when authenticating the client to a service.</span></span>  
  
<span data-ttu-id="64208-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="64208-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="64208-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="64208-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="64208-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="64208-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="64208-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="64208-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="64208-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="64208-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="64208-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="64208-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="64208-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpDigest >**</span><span class="sxs-lookup"><span data-stu-id="64208-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpDigest>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64208-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64208-111">Syntax</span></span>  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64208-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="64208-112">Attributes and Elements</span></span>  
 <span data-ttu-id="64208-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="64208-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64208-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="64208-114">Attributes</span></span>  
  
|<span data-ttu-id="64208-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="64208-115">Attribute</span></span>|<span data-ttu-id="64208-116">Popis</span><span class="sxs-lookup"><span data-stu-id="64208-116">Description</span></span>|  
|---------------|-----------------|  
|`impersonationLevel`|<span data-ttu-id="64208-117">Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="64208-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="64208-118">Režim zosobnění, který klient vybere, není na serveru vynutil.</span><span class="sxs-lookup"><span data-stu-id="64208-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="64208-119">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="64208-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="64208-120">Identifikace Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="64208-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="64208-121">Zosobnění Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="64208-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="64208-122">Delegování Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="64208-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="64208-123">Anonymous Server nemůže zosobnit nebo identifikovat klienta.</span><span class="sxs-lookup"><span data-stu-id="64208-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="64208-124">NTato Úroveň zosobnění není přiřazena.</span><span class="sxs-lookup"><span data-stu-id="64208-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="64208-125">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="64208-125">The default is Identification.</span></span> <span data-ttu-id="64208-126">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="64208-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64208-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="64208-127">Child Elements</span></span>  
 <span data-ttu-id="64208-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="64208-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64208-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="64208-129">Parent Elements</span></span>  
  
|<span data-ttu-id="64208-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="64208-130">Element</span></span>|<span data-ttu-id="64208-131">Popis</span><span class="sxs-lookup"><span data-stu-id="64208-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64208-132">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="64208-132">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="64208-133">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="64208-133">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64208-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64208-134">Remarks</span></span>  
 <span data-ttu-id="64208-135">Výtah je hodnota hash určená pomocí algoritmu a sady vstupů.</span><span class="sxs-lookup"><span data-stu-id="64208-135">A digest is a hash determined by using an algorithm and a set of inputs.</span></span> <span data-ttu-id="64208-136">Ověřovatel a ověřené souhlas s algoritmem a vyměňují data použitá jako vstupy.</span><span class="sxs-lookup"><span data-stu-id="64208-136">The authenticator and the authenticated agree upon an algorithm and exchange the data used as inputs.</span></span> <span data-ttu-id="64208-137">Klient může vypočítat hodnotu hash a odeslat ji do služby.</span><span class="sxs-lookup"><span data-stu-id="64208-137">The client can calculate the hash and send it to the service.</span></span> <span data-ttu-id="64208-138">Služba také vypočítá hodnotu hash a porovná hodnoty.</span><span class="sxs-lookup"><span data-stu-id="64208-138">The service also calculates the hash and compares the values.</span></span> <span data-ttu-id="64208-139">Shoda ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="64208-139">A match validates the client.</span></span>  
  
 <span data-ttu-id="64208-140">Tato funkce musí být povolená se službou Active Directory ve Windows a Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="64208-140">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="64208-141">Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).</span><span class="sxs-lookup"><span data-stu-id="64208-141">For more information, see [Digest Authentication in IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64208-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64208-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [<span data-ttu-id="64208-143">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="64208-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="64208-144">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="64208-144">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="64208-145">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="64208-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="64208-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="64208-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
