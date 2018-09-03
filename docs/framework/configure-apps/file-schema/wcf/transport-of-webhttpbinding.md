---
title: '&lt;transport&gt; – &lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: bbbd459e5717722359fe010a27e548d21ff074db
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482674"
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="2d5cf-102">&lt;transport&gt; – &lt;webHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2d5cf-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="2d5cf-103">Definuje nastavení zabezpečení na úrovni přenosu pro koncový bod služby nakonfigurovaný tak, aby přijímal požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="2d5cf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2d5cf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2d5cf-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="2d5cf-105">\<bindings></span></span>  
<span data-ttu-id="2d5cf-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="2d5cf-106">\<webHttpBinding></span></span>  
<span data-ttu-id="2d5cf-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2d5cf-107">\<binding></span></span>  
<span data-ttu-id="2d5cf-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="2d5cf-108">\<security></span></span>  
<span data-ttu-id="2d5cf-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="2d5cf-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d5cf-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d5cf-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="2d5cf-111">Typ</span><span class="sxs-lookup"><span data-stu-id="2d5cf-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d5cf-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2d5cf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2d5cf-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d5cf-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="2d5cf-114">Attributes</span></span>  
  
|<span data-ttu-id="2d5cf-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="2d5cf-115">Attribute</span></span>|<span data-ttu-id="2d5cf-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2d5cf-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="2d5cf-117">Určuje přihlašovací údaje pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="2d5cf-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="2d5cf-119">Určuje přihlašovací údaje pro ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="2d5cf-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="2d5cf-121">Řetězec určující sféru ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="2d5cf-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2d5cf-123">Sféra ověření určuje nejméně název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="2d5cf-124">Můžete také určit kolekci uživatelů, který má přístup.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="2d5cf-125">Sféra ověření pro ověření, který z nich několik možných uživatelská jména a hesla je možné dotazovat uživatele.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="2d5cf-126">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="2d5cf-127">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="2d5cf-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="2d5cf-128">2.  WhenSupported – zásady se vynucuje jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="2d5cf-129">3.  Vždy – je vždy zásady vynucují.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="2d5cf-130">K ověření se nezdaří klientů, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="2d5cf-131">Typ clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="2d5cf-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2d5cf-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2d5cf-132">Value</span></span>|<span data-ttu-id="2d5cf-133">Popis</span><span class="sxs-lookup"><span data-stu-id="2d5cf-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2d5cf-134">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2d5cf-135">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="2d5cf-136">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="2d5cf-137">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2d5cf-138">Ověřování protokolem NTLM se používá jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2d5cf-139">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="2d5cf-140">proxyCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="2d5cf-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2d5cf-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2d5cf-141">Value</span></span>|<span data-ttu-id="2d5cf-142">Popis</span><span class="sxs-lookup"><span data-stu-id="2d5cf-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="2d5cf-143">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="2d5cf-144">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="2d5cf-145">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="2d5cf-146">Používá NTLM jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="2d5cf-147">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d5cf-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2d5cf-148">Child Elements</span></span>  
 <span data-ttu-id="2d5cf-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="2d5cf-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d5cf-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2d5cf-150">Parent Elements</span></span>  
  
|<span data-ttu-id="2d5cf-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="2d5cf-151">Element</span></span>|<span data-ttu-id="2d5cf-152">Popis</span><span class="sxs-lookup"><span data-stu-id="2d5cf-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2d5cf-153">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="2d5cf-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="2d5cf-154">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="2d5cf-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d5cf-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d5cf-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="2d5cf-156">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2d5cf-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2d5cf-157">Vazby</span><span class="sxs-lookup"><span data-stu-id="2d5cf-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2d5cf-158">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="2d5cf-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2d5cf-159">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="2d5cf-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2d5cf-160">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2d5cf-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="2d5cf-161">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="2d5cf-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
