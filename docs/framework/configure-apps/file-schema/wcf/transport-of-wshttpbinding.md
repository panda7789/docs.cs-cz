---
title: '&lt;transport&gt; – &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: d6095c2cc9a315855db03f3a3f44547b1f64b9df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a><span data-ttu-id="78f21-102">&lt;transport&gt; – &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="78f21-102">&lt;transport&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="78f21-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="78f21-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="78f21-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="78f21-104">\<system.serviceModel></span></span>  
<span data-ttu-id="78f21-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="78f21-105">\<bindings></span></span>  
<span data-ttu-id="78f21-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="78f21-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="78f21-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="78f21-107">\<binding></span></span>  
<span data-ttu-id="78f21-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="78f21-108">\<security></span></span>  
<span data-ttu-id="78f21-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="78f21-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f21-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78f21-110">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="78f21-111">Typ</span><span class="sxs-lookup"><span data-stu-id="78f21-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78f21-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="78f21-112">Attributes and Elements</span></span>  
 <span data-ttu-id="78f21-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="78f21-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78f21-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="78f21-114">Attributes</span></span>  
  
|<span data-ttu-id="78f21-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="78f21-115">Attribute</span></span>|<span data-ttu-id="78f21-116">Popis</span><span class="sxs-lookup"><span data-stu-id="78f21-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="78f21-117">Určuje, že pověření použitá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="78f21-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="78f21-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="78f21-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="78f21-119">Určuje, že pověření použitá k ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="78f21-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="78f21-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="78f21-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="78f21-121">Řetězec, který určuje sféru ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="78f21-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="78f21-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="78f21-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="78f21-123">Sféra ověření určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="78f21-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="78f21-124">Můžete také specifikovat kolekci uživatelů, který má přístup.</span><span class="sxs-lookup"><span data-stu-id="78f21-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="78f21-125">Uživatele můžete dotazovat sféry ověření, který z nich několik možných uživatelská jména a hesla je možné zjistit.</span><span class="sxs-lookup"><span data-stu-id="78f21-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="78f21-126">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="78f21-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="78f21-127">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="78f21-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="78f21-128">2.  WhenSupported – zásady se vynucují jenom v případě, že klient podporuje rozšířené ochrany.</span><span class="sxs-lookup"><span data-stu-id="78f21-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="78f21-129">3.  Vždy – je vždy tato zásada vynucená.</span><span class="sxs-lookup"><span data-stu-id="78f21-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="78f21-130">Klienti, které nepodporují rozšířené ochrany se nepodaří ověřit.</span><span class="sxs-lookup"><span data-stu-id="78f21-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="78f21-131">clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="78f21-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="78f21-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="78f21-132">Value</span></span>|<span data-ttu-id="78f21-133">Popis</span><span class="sxs-lookup"><span data-stu-id="78f21-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="78f21-134">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="78f21-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="78f21-135">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="78f21-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="78f21-136">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="78f21-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="78f21-137">Ověřování protokolem NTLM se používá jako nouzové řešení s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="78f21-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="78f21-138">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="78f21-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="78f21-139">K ověření klienta používá certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="78f21-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="78f21-140">proxyCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="78f21-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="78f21-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="78f21-141">Value</span></span>|<span data-ttu-id="78f21-142">Popis</span><span class="sxs-lookup"><span data-stu-id="78f21-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="78f21-143">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="78f21-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="78f21-144">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="78f21-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="78f21-145">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="78f21-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="78f21-146">Používá protokol NTLM jako nouzové řešení s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="78f21-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="78f21-147">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="78f21-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="78f21-148">K ověření klienta používá certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="78f21-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78f21-149">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="78f21-149">Child Elements</span></span>  
 <span data-ttu-id="78f21-150">Žádné</span><span class="sxs-lookup"><span data-stu-id="78f21-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="78f21-151">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="78f21-151">Parent Elements</span></span>  
  
|<span data-ttu-id="78f21-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="78f21-152">Element</span></span>|<span data-ttu-id="78f21-153">Popis</span><span class="sxs-lookup"><span data-stu-id="78f21-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78f21-154">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="78f21-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="78f21-155">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="78f21-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78f21-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="78f21-156">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="78f21-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="78f21-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="78f21-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="78f21-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="78f21-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="78f21-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="78f21-160">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="78f21-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="78f21-161">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="78f21-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
