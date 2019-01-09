---
title: '&lt;windows&gt; elementu &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 780d73b747feae5495ad08cb2324e7d8f8de0d7d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147470"
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="d7d73-102">&lt;windows&gt; elementu &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="d7d73-102">&lt;windows&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="d7d73-103">Určuje nastavení pro přihlašovací údaje Windows k provádět reprezentovalo klienta.</span><span class="sxs-lookup"><span data-stu-id="d7d73-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="d7d73-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d7d73-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d7d73-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d7d73-105">\<behaviors></span></span>  
<span data-ttu-id="d7d73-106">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d7d73-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d7d73-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d7d73-107">\<behavior></span></span>  
<span data-ttu-id="d7d73-108">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d7d73-108">\<clientCredentials></span></span>  
<span data-ttu-id="d7d73-109">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="d7d73-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d73-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7d73-110">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7d73-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d7d73-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d7d73-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d7d73-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7d73-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d7d73-113">Attributes</span></span>  
  
|<span data-ttu-id="d7d73-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d7d73-114">Attribute</span></span>|<span data-ttu-id="d7d73-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d7d73-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="d7d73-116">Nastavuje předvolbu zosobnění, který klient komunikuje na server.</span><span class="sxs-lookup"><span data-stu-id="d7d73-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="d7d73-117">Režim zosobnění, který klient vybere nevynucuje na serveru.</span><span class="sxs-lookup"><span data-stu-id="d7d73-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="d7d73-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="d7d73-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d7d73-119">-Identifikace: Na serveru můžete získat identit a oprávnění klienta, ale nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="d7d73-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="d7d73-120">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="d7d73-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="d7d73-121">-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="d7d73-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="d7d73-122">-Anonymní: Server nelze zosobnit nebo identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="d7d73-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="d7d73-123">-Žádný: Úroveň zosobnění není přiřazen.</span><span class="sxs-lookup"><span data-stu-id="d7d73-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="d7d73-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="d7d73-124">The default is Identification.</span></span> <span data-ttu-id="d7d73-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="d7d73-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="d7d73-126">Nastavení této vlastnosti na `true` umožňuje ověřování na starší verzi NTLM, pokud není k dispozici protokol Kerberos.</span><span class="sxs-lookup"><span data-stu-id="d7d73-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="d7d73-127">Nastavení této vlastnosti na `false` způsobí, že Windows Communication Foundation (WCF), aby se snažíme vyvolá výjimku, pokud je použit protokol NTLM.</span><span class="sxs-lookup"><span data-stu-id="d7d73-127">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="d7d73-128">Všimněte si, že nastavení této vlastnosti na `false` nemůže zabránit odeslání při přenosu přihlašovacích údajů protokolů NTLM.</span><span class="sxs-lookup"><span data-stu-id="d7d73-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7d73-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d7d73-129">Child Elements</span></span>  
 <span data-ttu-id="d7d73-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="d7d73-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7d73-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d7d73-131">Parent Elements</span></span>  
  
|<span data-ttu-id="d7d73-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="d7d73-132">Element</span></span>|<span data-ttu-id="d7d73-133">Popis</span><span class="sxs-lookup"><span data-stu-id="d7d73-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7d73-134">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="d7d73-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="d7d73-135">Určuje pověření pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="d7d73-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7d73-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7d73-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [<span data-ttu-id="d7d73-137">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="d7d73-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="d7d73-138">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="d7d73-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="d7d73-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d7d73-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
