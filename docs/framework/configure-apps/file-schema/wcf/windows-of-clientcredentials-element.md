---
title: <windows> z <clientCredentials> – Element
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: b5e92745b9e39534d2a0bc35504c2dbc8346d2ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221017"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="87cd2-102">\<Windows > z \<clientCredentials > – Element</span><span class="sxs-lookup"><span data-stu-id="87cd2-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="87cd2-103">Určuje nastavení pro přihlašovací údaje Windows k provádět reprezentovalo klienta.</span><span class="sxs-lookup"><span data-stu-id="87cd2-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="87cd2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87cd2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87cd2-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="87cd2-105">\<behaviors></span></span>  
<span data-ttu-id="87cd2-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="87cd2-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="87cd2-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="87cd2-107">\<behavior></span></span>  
<span data-ttu-id="87cd2-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="87cd2-108">\<clientCredentials></span></span>  
<span data-ttu-id="87cd2-109">\<windows></span><span class="sxs-lookup"><span data-stu-id="87cd2-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87cd2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87cd2-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87cd2-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87cd2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="87cd2-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87cd2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87cd2-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="87cd2-113">Attributes</span></span>  
  
|<span data-ttu-id="87cd2-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="87cd2-114">Attribute</span></span>|<span data-ttu-id="87cd2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="87cd2-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="87cd2-116">Nastavuje předvolbu zosobnění, který klient komunikuje na server.</span><span class="sxs-lookup"><span data-stu-id="87cd2-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="87cd2-117">Režim zosobnění, který klient vybere nevynucuje na serveru.</span><span class="sxs-lookup"><span data-stu-id="87cd2-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="87cd2-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="87cd2-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="87cd2-119">-Identifikace: Na serveru můžete získat identit a oprávnění klienta, ale nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="87cd2-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="87cd2-120">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="87cd2-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="87cd2-121">-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="87cd2-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="87cd2-122">-Anonymní: Server nelze zosobnit nebo identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="87cd2-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="87cd2-123">-Žádný: Úroveň zosobnění není přiřazen.</span><span class="sxs-lookup"><span data-stu-id="87cd2-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="87cd2-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="87cd2-124">The default is Identification.</span></span> <span data-ttu-id="87cd2-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="87cd2-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="87cd2-126">Nastavení této vlastnosti na `true` umožňuje ověřování na starší verzi NTLM, pokud není k dispozici protokol Kerberos.</span><span class="sxs-lookup"><span data-stu-id="87cd2-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="87cd2-127">Nastavení této vlastnosti na `false` způsobí, že Windows Communication Foundation (WCF), aby se snažíme vyvolá výjimku, pokud je použit protokol NTLM.</span><span class="sxs-lookup"><span data-stu-id="87cd2-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="87cd2-128">Všimněte si, že nastavení této vlastnosti na `false` nemůže zabránit odeslání při přenosu přihlašovacích údajů protokolů NTLM.</span><span class="sxs-lookup"><span data-stu-id="87cd2-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87cd2-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="87cd2-129">Child Elements</span></span>  
 <span data-ttu-id="87cd2-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="87cd2-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87cd2-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="87cd2-131">Parent Elements</span></span>  
  
|<span data-ttu-id="87cd2-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="87cd2-132">Element</span></span>|<span data-ttu-id="87cd2-133">Popis</span><span class="sxs-lookup"><span data-stu-id="87cd2-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87cd2-134">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="87cd2-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="87cd2-135">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="87cd2-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87cd2-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87cd2-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="87cd2-137">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="87cd2-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="87cd2-138">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="87cd2-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="87cd2-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="87cd2-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
