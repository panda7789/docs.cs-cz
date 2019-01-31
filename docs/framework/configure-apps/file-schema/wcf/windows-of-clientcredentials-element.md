---
title: <windows> z <clientCredentials> – Element
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: fb55fb9901e4c08a3c5d7662fdb3bf12a71876bb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275155"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="97704-102">\<Windows > z \<clientCredentials > – Element</span><span class="sxs-lookup"><span data-stu-id="97704-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="97704-103">Určuje nastavení pro přihlašovací údaje Windows k provádět reprezentovalo klienta.</span><span class="sxs-lookup"><span data-stu-id="97704-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="97704-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="97704-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="97704-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="97704-105">\<behaviors></span></span>  
<span data-ttu-id="97704-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="97704-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="97704-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="97704-107">\<behavior></span></span>  
<span data-ttu-id="97704-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="97704-108">\<clientCredentials></span></span>  
<span data-ttu-id="97704-109">\<windows></span><span class="sxs-lookup"><span data-stu-id="97704-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97704-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97704-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97704-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="97704-111">Attributes and Elements</span></span>  
 <span data-ttu-id="97704-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="97704-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97704-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="97704-113">Attributes</span></span>  
  
|<span data-ttu-id="97704-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="97704-114">Attribute</span></span>|<span data-ttu-id="97704-115">Popis</span><span class="sxs-lookup"><span data-stu-id="97704-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="97704-116">Nastavuje předvolbu zosobnění, který klient komunikuje na server.</span><span class="sxs-lookup"><span data-stu-id="97704-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="97704-117">Režim zosobnění, který klient vybere nevynucuje na serveru.</span><span class="sxs-lookup"><span data-stu-id="97704-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="97704-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="97704-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="97704-119">-Identifikace: Na serveru můžete získat identit a oprávnění klienta, ale nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="97704-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="97704-120">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="97704-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="97704-121">-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="97704-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="97704-122">-Anonymní: Server nelze zosobnit nebo identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="97704-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="97704-123">-Žádný: Úroveň zosobnění není přiřazen.</span><span class="sxs-lookup"><span data-stu-id="97704-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="97704-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="97704-124">The default is Identification.</span></span> <span data-ttu-id="97704-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="97704-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="97704-126">Nastavení této vlastnosti na `true` umožňuje ověřování na starší verzi NTLM, pokud není k dispozici protokol Kerberos.</span><span class="sxs-lookup"><span data-stu-id="97704-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="97704-127">Nastavení této vlastnosti na `false` způsobí, že Windows Communication Foundation (WCF), aby se snažíme vyvolá výjimku, pokud je použit protokol NTLM.</span><span class="sxs-lookup"><span data-stu-id="97704-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="97704-128">Všimněte si, že nastavení této vlastnosti na `false` nemůže zabránit odeslání při přenosu přihlašovacích údajů protokolů NTLM.</span><span class="sxs-lookup"><span data-stu-id="97704-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97704-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="97704-129">Child Elements</span></span>  
 <span data-ttu-id="97704-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="97704-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97704-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="97704-131">Parent Elements</span></span>  
  
|<span data-ttu-id="97704-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="97704-132">Element</span></span>|<span data-ttu-id="97704-133">Popis</span><span class="sxs-lookup"><span data-stu-id="97704-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97704-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="97704-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="97704-135">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="97704-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97704-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97704-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="97704-137">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="97704-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="97704-138">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="97704-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="97704-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="97704-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
