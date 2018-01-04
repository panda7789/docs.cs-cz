---
title: '&lt;windows&gt; elementu &lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6687f93be26dedcb34f08770708c072742fdd4de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltwindowsgt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="5fa0c-102">&lt;windows&gt; elementu &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="5fa0c-102">&lt;windows&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="5fa0c-103">Určuje nastavení pro pověření systému Windows, který se má použít k reprezentování klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
 <span data-ttu-id="5fa0c-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5fa0c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5fa0c-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5fa0c-105">\<behaviors></span></span>  
<span data-ttu-id="5fa0c-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5fa0c-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5fa0c-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="5fa0c-107">\<behavior></span></span>  
<span data-ttu-id="5fa0c-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5fa0c-108">\<clientCredentials></span></span>  
<span data-ttu-id="5fa0c-109">\<Windows ></span><span class="sxs-lookup"><span data-stu-id="5fa0c-109">\<windows></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fa0c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fa0c-110">Syntax</span></span>  
  
```xml  
<windows   
    allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"  
        allowNtlm="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fa0c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5fa0c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5fa0c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fa0c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5fa0c-113">Attributes</span></span>  
  
|<span data-ttu-id="5fa0c-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="5fa0c-114">Attribute</span></span>|<span data-ttu-id="5fa0c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5fa0c-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="5fa0c-116">Nastaví zosobnění předvoleb, které klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-116">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="5fa0c-117">Režim zosobnění, který klient vybere nevynucuje na serveru.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-117">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="5fa0c-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="5fa0c-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5fa0c-119">-Identifikace: Na serveru můžete získat identitu a oprávnění klienta, ale nelze zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-119">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="5fa0c-120">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-120">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="5fa0c-121">-Delegování: Server může zosobnit kontext zabezpečení klienta na vzdálené systémy.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-121">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="5fa0c-122">-Anonymní: Server nelze zosobnit nebo identifikaci klienta.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-122">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="5fa0c-123">-None: Není přiřazen úroveň zosobnění.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-123">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="5fa0c-124">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-124">The default is Identification.</span></span> <span data-ttu-id="5fa0c-125">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-125">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="5fa0c-126">Nastavení této vlastnosti na `true` povoluje ověřování na starší verzi protokolu NTLM, pokud není k dispozici protokolu Kerberos.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-126">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="5fa0c-127">Nastavení této vlastnosti na `false` způsobí, že [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aby best effort vyvolá výjimku, pokud se používá protokol NTLM.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-127">Setting this property to `false` causes [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="5fa0c-128">Všimněte si, že nastavení této vlastnosti na `false` nemusí zabránit odesílány prostřednictvím sítě pověření NTLM.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-128">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fa0c-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5fa0c-129">Child Elements</span></span>  
 <span data-ttu-id="5fa0c-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="5fa0c-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fa0c-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5fa0c-131">Parent Elements</span></span>  
  
|<span data-ttu-id="5fa0c-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="5fa0c-132">Element</span></span>|<span data-ttu-id="5fa0c-133">Popis</span><span class="sxs-lookup"><span data-stu-id="5fa0c-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fa0c-134">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5fa0c-134">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="5fa0c-135">Určuje pověření, která používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="5fa0c-135">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5fa0c-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fa0c-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsClientElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 [<span data-ttu-id="5fa0c-137">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="5fa0c-137">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="5fa0c-138">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="5fa0c-138">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="5fa0c-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5fa0c-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
