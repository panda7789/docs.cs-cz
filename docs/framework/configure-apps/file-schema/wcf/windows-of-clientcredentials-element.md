---
title: <windows><clientCredentials>elementu
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: 61ca99213f0b83a5af5df0184a8c1de405366288
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399120"
---
# <a name="windows-of-clientcredentials-element"></a><span data-ttu-id="f8e30-102">\<windows>\<clientCredentials>elementu</span><span class="sxs-lookup"><span data-stu-id="f8e30-102">\<windows> of \<clientCredentials> Element</span></span>
<span data-ttu-id="f8e30-103">Určuje nastavení pro přihlašovací údaje systému Windows, které se mají použít k reprezentaci klienta.</span><span class="sxs-lookup"><span data-stu-id="f8e30-103">Specifies the settings for a Windows credential to be used to represent the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windows>**  
  
## <a name="syntax"></a><span data-ttu-id="f8e30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8e30-104">Syntax</span></span>  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8e30-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f8e30-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f8e30-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f8e30-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8e30-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f8e30-107">Attributes</span></span>  
  
|<span data-ttu-id="f8e30-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="f8e30-108">Attribute</span></span>|<span data-ttu-id="f8e30-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f8e30-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|<span data-ttu-id="f8e30-110">Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem.</span><span class="sxs-lookup"><span data-stu-id="f8e30-110">Sets the impersonation preference that the client communicates to the server.</span></span> <span data-ttu-id="f8e30-111">Režim zosobnění, který klient vybere, není na serveru vynutil.</span><span class="sxs-lookup"><span data-stu-id="f8e30-111">The impersonation mode that the client selects is not enforced on the server.</span></span> <span data-ttu-id="f8e30-112">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f8e30-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f8e30-113">-Identifikace: Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.</span><span class="sxs-lookup"><span data-stu-id="f8e30-113">-   Identification: The server can get the identity and privileges of the client, but cannot impersonate the client.</span></span><br /><span data-ttu-id="f8e30-114">-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.</span><span class="sxs-lookup"><span data-stu-id="f8e30-114">-   Impersonation: The server can impersonate the client's security context on the local system.</span></span><br /><span data-ttu-id="f8e30-115">-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.</span><span class="sxs-lookup"><span data-stu-id="f8e30-115">-   Delegation: The server can impersonate the client's security context on remote systems.</span></span><br /><span data-ttu-id="f8e30-116">-Anonymní: Server nemůže zosobnit nebo identifikovat klienta.</span><span class="sxs-lookup"><span data-stu-id="f8e30-116">-   Anonymous: The server cannot impersonate or identify the client.</span></span><br /><span data-ttu-id="f8e30-117">-None: úroveň zosobnění není přiřazena.</span><span class="sxs-lookup"><span data-stu-id="f8e30-117">-   None: An impersonation level is not assigned.</span></span><br /><br /> <span data-ttu-id="f8e30-118">Výchozí hodnota je identifikace.</span><span class="sxs-lookup"><span data-stu-id="f8e30-118">The default is Identification.</span></span> <span data-ttu-id="f8e30-119">Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="f8e30-119">This attribute is of type <xref:System.Security.Principal.TokenImpersonationLevel>.</span></span>|  
|`allowNtlm`|<span data-ttu-id="f8e30-120">Nastavením této vlastnosti umožníte, aby se `true` ověřování downgradal na NTLM, pokud není k dispozici protokol Kerberos.</span><span class="sxs-lookup"><span data-stu-id="f8e30-120">Setting this property to `true` allows authentication to downgrade to NTLM if Kerberos is not available.</span></span><br /><br /> <span data-ttu-id="f8e30-121">Nastavení této vlastnosti na `false` způsobí, že Windows Communication Foundation (WCF) vyvolá výjimku, pokud se používá protokol NTLM.</span><span class="sxs-lookup"><span data-stu-id="f8e30-121">Setting this property to `false` causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="f8e30-122">Všimněte si, že nastavení této vlastnosti na `false` nemusí bránit v posílání přihlašovacích údajů NTLM přes tento kabel.</span><span class="sxs-lookup"><span data-stu-id="f8e30-122">Note that setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8e30-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f8e30-123">Child Elements</span></span>  
 <span data-ttu-id="f8e30-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="f8e30-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8e30-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f8e30-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f8e30-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8e30-126">Element</span></span>|<span data-ttu-id="f8e30-127">Description</span><span class="sxs-lookup"><span data-stu-id="f8e30-127">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="f8e30-128">Určuje přihlašovací údaje, které se použijí k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="f8e30-128">Specifies the credentials used to authenticate the client to the service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8e30-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8e30-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [<span data-ttu-id="f8e30-130">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="f8e30-130">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="f8e30-131">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="f8e30-131">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f8e30-132">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f8e30-132">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
