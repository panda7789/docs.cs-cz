---
title: <windows><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940299"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="438bc-102">\<> \<prvku ClientCredentials > elementu Windows</span><span class="sxs-lookup"><span data-stu-id="438bc-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="438bc-103">Určuje nastavení pro přihlašovací údaje systému Windows, které se mají použít k reprezentaci klienta.</span><span class="sxs-lookup"><span data-stu-id="438bc-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="438bc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="438bc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="438bc-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="438bc-105">\<behaviors></span></span>  
<span data-ttu-id="438bc-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="438bc-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="438bc-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="438bc-107">\<behavior></span></span>  
<span data-ttu-id="438bc-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="438bc-108">\<clientCredentials></span></span>  
<span data-ttu-id="438bc-109">\<windows></span><span class="sxs-lookup"><span data-stu-id="438bc-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438bc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="438bc-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="438bc-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="438bc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="438bc-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="438bc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="438bc-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="438bc-113">Attributes</span></span>  
  
|<span data-ttu-id="438bc-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="438bc-114">Attribute</span></span>|<span data-ttu-id="438bc-115">Popis</span><span class="sxs-lookup"><span data-stu-id="438bc-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="438bc-116">Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="438bc-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="438bc-117">Režim zosobnění, který klient vybere, není na serveru vynutil.</span><span class="sxs-lookup"><span data-stu-id="438bc-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="438bc-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="438bc-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="438bc-119">Identifikace Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="438bc-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="438bc-120">Zosobnění Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="438bc-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="438bc-121">Delegování Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="438bc-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="438bc-122">Anonymous Server nemůže zosobnit nebo identifikovat klienta.</span><span class="sxs-lookup"><span data-stu-id="438bc-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="438bc-123">NTato Úroveň zosobnění není přiřazena.</span><span class="sxs-lookup"><span data-stu-id="438bc-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="438bc-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="438bc-124">The default is Identification.</span></span> <span data-ttu-id="438bc-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="438bc-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="438bc-126">Nastavením této vlastnosti `true` umožníte, aby se ověřování downgradal na NTLM, pokud není k dispozici protokol Kerberos.</span><span class="sxs-lookup"><span data-stu-id="438bc-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="438bc-127">Nastavení této vlastnosti na `false` způsobí, že Windows Communication Foundation (WCF) vyvolá výjimku, pokud se používá protokol NTLM.</span><span class="sxs-lookup"><span data-stu-id="438bc-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="438bc-128">Všimněte si, že nastavení této `false` vlastnosti na nemusí bránit v posílání přihlašovacích údajů NTLM přes tento kabel.</span><span class="sxs-lookup"><span data-stu-id="438bc-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="438bc-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="438bc-129">Child Elements</span></span>  
 <span data-ttu-id="438bc-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="438bc-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="438bc-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="438bc-131">Parent Elements</span></span>  
  
|<span data-ttu-id="438bc-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="438bc-132">Element</span></span>|<span data-ttu-id="438bc-133">Popis</span><span class="sxs-lookup"><span data-stu-id="438bc-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="438bc-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="438bc-134">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="438bc-135">Určuje přihlašovací údaje, které se použijí k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="438bc-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="438bc-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="438bc-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="438bc-137">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="438bc-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="438bc-138">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="438bc-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="438bc-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="438bc-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
