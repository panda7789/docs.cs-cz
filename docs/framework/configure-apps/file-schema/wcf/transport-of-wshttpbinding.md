---
title: '&lt;transport&gt; – &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 5a62eefa6865a6908caecef87b0e457040df0b21
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850150"
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a><span data-ttu-id="926e0-102">&lt;transport&gt; – &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="926e0-102">&lt;transport&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="926e0-103">Definuje nastavení ověřování pro přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="926e0-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="926e0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="926e0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="926e0-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="926e0-105">\<bindings></span></span>  
<span data-ttu-id="926e0-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="926e0-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="926e0-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="926e0-107">\<binding></span></span>  
<span data-ttu-id="926e0-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="926e0-108">\<security></span></span>  
<span data-ttu-id="926e0-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="926e0-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="926e0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="926e0-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="926e0-111">Typ</span><span class="sxs-lookup"><span data-stu-id="926e0-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="926e0-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="926e0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="926e0-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="926e0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="926e0-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="926e0-114">Attributes</span></span>  
  
|<span data-ttu-id="926e0-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="926e0-115">Attribute</span></span>|<span data-ttu-id="926e0-116">Popis</span><span class="sxs-lookup"><span data-stu-id="926e0-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="926e0-117">Určuje přihlašovací údaje pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="926e0-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="926e0-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="926e0-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="926e0-119">Určuje přihlašovací údaje pro ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="926e0-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="926e0-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="926e0-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="926e0-121">Řetězec určující sféru ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="926e0-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="926e0-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="926e0-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="926e0-123">Sféra ověření určuje nejméně název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="926e0-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="926e0-124">Můžete také určit kolekci uživatelů, který má přístup.</span><span class="sxs-lookup"><span data-stu-id="926e0-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="926e0-125">Sféra ověření pro ověření, který z nich několik možných uživatelská jména a hesla je možné dotazovat uživatele.</span><span class="sxs-lookup"><span data-stu-id="926e0-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="926e0-126">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="926e0-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="926e0-127">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="926e0-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="926e0-128">2.  WhenSupported – zásady se vynucuje jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="926e0-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="926e0-129">3.  Vždy – je vždy zásady vynucují.</span><span class="sxs-lookup"><span data-stu-id="926e0-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="926e0-130">K ověření se nezdaří klientů, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="926e0-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="926e0-131">Typ clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="926e0-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="926e0-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="926e0-132">Value</span></span>|<span data-ttu-id="926e0-133">Popis</span><span class="sxs-lookup"><span data-stu-id="926e0-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="926e0-134">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="926e0-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="926e0-135">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="926e0-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="926e0-136">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="926e0-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="926e0-137">Ověřování protokolem NTLM se používá jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="926e0-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="926e0-138">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="926e0-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="926e0-139">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="926e0-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="926e0-140">proxyCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="926e0-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="926e0-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="926e0-141">Value</span></span>|<span data-ttu-id="926e0-142">Popis</span><span class="sxs-lookup"><span data-stu-id="926e0-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="926e0-143">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="926e0-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="926e0-144">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="926e0-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="926e0-145">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="926e0-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="926e0-146">Používá NTLM jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="926e0-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="926e0-147">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="926e0-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="926e0-148">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="926e0-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="926e0-149">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="926e0-149">Child Elements</span></span>  
 <span data-ttu-id="926e0-150">Žádné</span><span class="sxs-lookup"><span data-stu-id="926e0-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="926e0-151">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="926e0-151">Parent Elements</span></span>  
  
|<span data-ttu-id="926e0-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="926e0-152">Element</span></span>|<span data-ttu-id="926e0-153">Popis</span><span class="sxs-lookup"><span data-stu-id="926e0-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="926e0-154">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="926e0-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="926e0-155">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="926e0-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="926e0-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="926e0-156">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="926e0-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="926e0-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="926e0-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="926e0-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="926e0-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="926e0-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="926e0-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="926e0-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="926e0-161">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="926e0-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
