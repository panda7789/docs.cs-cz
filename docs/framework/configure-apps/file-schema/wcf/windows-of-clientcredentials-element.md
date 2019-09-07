---
title: <windows><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399120"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="490fd-102">\<> \<prvku ClientCredentials > elementu Windows</span><span class="sxs-lookup"><span data-stu-id="490fd-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="490fd-103">Určuje nastavení pro přihlašovací údaje systému Windows, které se mají použít k reprezentaci klienta.</span><span class="sxs-lookup"><span data-stu-id="490fd-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
<span data-ttu-id="490fd-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="490fd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="490fd-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="490fd-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="490fd-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="490fd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="490fd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="490fd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="490fd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="490fd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="490fd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="490fd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="490fd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Windows**</span><span class="sxs-lookup"><span data-stu-id="490fd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="490fd-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="490fd-111">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="490fd-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="490fd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="490fd-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="490fd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="490fd-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="490fd-114">Attributes</span></span>  
  
|<span data-ttu-id="490fd-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="490fd-115">Attribute</span></span>|<span data-ttu-id="490fd-116">Popis</span><span class="sxs-lookup"><span data-stu-id="490fd-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="490fd-117">Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="490fd-117">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="490fd-118">Režim zosobnění, který klient vybere, není na serveru vynutil.</span><span class="sxs-lookup"><span data-stu-id="490fd-118">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="490fd-119">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="490fd-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="490fd-120">Identifikace Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="490fd-120">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="490fd-121">Zosobnění Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="490fd-121">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="490fd-122">Delegování Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="490fd-122">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="490fd-123">Anonymous Server nemůže zosobnit nebo identifikovat klienta.</span><span class="sxs-lookup"><span data-stu-id="490fd-123">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="490fd-124">NTato Úroveň zosobnění není přiřazena.</span><span class="sxs-lookup"><span data-stu-id="490fd-124">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="490fd-125">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="490fd-125">The default is Identification.</span></span> <span data-ttu-id="490fd-126">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.</span><span class="sxs-lookup"><span data-stu-id="490fd-126">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="490fd-127">Nastavením této vlastnosti `true` umožníte, aby se ověřování downgradal na NTLM, pokud není k dispozici protokol Kerberos.</span><span class="sxs-lookup"><span data-stu-id="490fd-127">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="490fd-128">Nastavení této vlastnosti na `false` způsobí, že Windows Communication Foundation (WCF) vyvolá výjimku, pokud se používá protokol NTLM.</span><span class="sxs-lookup"><span data-stu-id="490fd-128">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="490fd-129">Všimněte si, že nastavení této `false` vlastnosti na nemusí bránit v posílání přihlašovacích údajů NTLM přes tento kabel.</span><span class="sxs-lookup"><span data-stu-id="490fd-129">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="490fd-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="490fd-130">Child Elements</span></span>  
 <span data-ttu-id="490fd-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="490fd-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="490fd-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="490fd-132">Parent Elements</span></span>  
  
|<span data-ttu-id="490fd-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="490fd-133">Element</span></span>|<span data-ttu-id="490fd-134">Popis</span><span class="sxs-lookup"><span data-stu-id="490fd-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="490fd-135">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="490fd-135">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="490fd-136">Určuje přihlašovací údaje, které se použijí k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="490fd-136">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="490fd-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="490fd-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="490fd-138">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="490fd-138">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="490fd-139">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="490fd-139">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="490fd-140">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="490fd-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
