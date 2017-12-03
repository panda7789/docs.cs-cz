---
title: "&lt;transport&gt; – &lt;webHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d5c0d17f756c4cca84a48cf6849c4d0945cc2b3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="fa4d2-102">&lt;transport&gt; – &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="fa4d2-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="fa4d2-103">Definuje nastavení zabezpečení na úrovni přenosu pro koncového bodu služby nastavena k přijímání požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="fa4d2-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fa4d2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa4d2-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="fa4d2-105">\<bindings></span></span>  
<span data-ttu-id="fa4d2-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="fa4d2-106">\<webHttpBinding></span></span>  
<span data-ttu-id="fa4d2-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="fa4d2-107">\<binding></span></span>  
<span data-ttu-id="fa4d2-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="fa4d2-108">\<security></span></span>  
<span data-ttu-id="fa4d2-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="fa4d2-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa4d2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa4d2-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="fa4d2-111">Typ</span><span class="sxs-lookup"><span data-stu-id="fa4d2-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa4d2-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fa4d2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fa4d2-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa4d2-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="fa4d2-114">Attributes</span></span>  
  
|<span data-ttu-id="fa4d2-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="fa4d2-115">Attribute</span></span>|<span data-ttu-id="fa4d2-116">Popis</span><span class="sxs-lookup"><span data-stu-id="fa4d2-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="fa4d2-117">Určuje, že pověření použitá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="fa4d2-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="fa4d2-119">Určuje, že pověření použitá k ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="fa4d2-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="fa4d2-121">Řetězec, který určuje sféru ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="fa4d2-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="fa4d2-123">Sféra ověření určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="fa4d2-124">Můžete také specifikovat kolekci uživatelů, který má přístup.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="fa4d2-125">Uživatele můžete dotazovat sféry ověření, který z nich několik možných uživatelská jména a hesla je možné zjistit.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="fa4d2-126">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="fa4d2-127">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="fa4d2-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="fa4d2-128">2.  WhenSupported – zásady se vynucují jenom v případě, že klient podporuje rozšířené ochrany.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="fa4d2-129">3.  Vždy – je vždy tato zásada vynucená.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="fa4d2-130">Klienti, které nepodporují rozšířené ochrany se nepodaří ověřit.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="fa4d2-131">clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="fa4d2-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="fa4d2-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fa4d2-132">Value</span></span>|<span data-ttu-id="fa4d2-133">Popis</span><span class="sxs-lookup"><span data-stu-id="fa4d2-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="fa4d2-134">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="fa4d2-135">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="fa4d2-136">K ověření klienta používá certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="fa4d2-137">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="fa4d2-138">Ověřování protokolem NTLM se používá jako nouzové řešení s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="fa4d2-139">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="fa4d2-140">proxyCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="fa4d2-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="fa4d2-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fa4d2-141">Value</span></span>|<span data-ttu-id="fa4d2-142">Popis</span><span class="sxs-lookup"><span data-stu-id="fa4d2-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="fa4d2-143">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="fa4d2-144">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="fa4d2-145">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="fa4d2-146">Používá protokol NTLM jako nouzové řešení s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="fa4d2-147">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa4d2-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fa4d2-148">Child Elements</span></span>  
 <span data-ttu-id="fa4d2-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="fa4d2-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa4d2-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fa4d2-150">Parent Elements</span></span>  
  
|<span data-ttu-id="fa4d2-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="fa4d2-151">Element</span></span>|<span data-ttu-id="fa4d2-152">Popis</span><span class="sxs-lookup"><span data-stu-id="fa4d2-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa4d2-153">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="fa4d2-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="fa4d2-154">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="fa4d2-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa4d2-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa4d2-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="fa4d2-156">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="fa4d2-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="fa4d2-157">Vazby</span><span class="sxs-lookup"><span data-stu-id="fa4d2-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fa4d2-158">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="fa4d2-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="fa4d2-159">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="fa4d2-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="fa4d2-160">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="fa4d2-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="fa4d2-161">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="fa4d2-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
