---
title: <transport> z <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 8dcd51cd248dbba3ccf60295cb1712167684328e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116279"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="40a96-102">\<přenos > z \<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="40a96-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="40a96-103">Definuje nastavení zabezpečení na úrovni přenosu pro koncový bod služby nakonfigurovaný tak, aby přijímal požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="40a96-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="40a96-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="40a96-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="40a96-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="40a96-105">\<bindings></span></span>  
<span data-ttu-id="40a96-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="40a96-106">\<webHttpBinding></span></span>  
<span data-ttu-id="40a96-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="40a96-107">\<binding></span></span>  
<span data-ttu-id="40a96-108">\<security></span><span class="sxs-lookup"><span data-stu-id="40a96-108">\<security></span></span>  
<span data-ttu-id="40a96-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="40a96-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40a96-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40a96-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</webHttpBinding>
```  
  
## <a name="type"></a><span data-ttu-id="40a96-111">Type</span><span class="sxs-lookup"><span data-stu-id="40a96-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40a96-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="40a96-112">Attributes and Elements</span></span>  
 <span data-ttu-id="40a96-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="40a96-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40a96-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="40a96-114">Attributes</span></span>  
  
|<span data-ttu-id="40a96-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="40a96-115">Attribute</span></span>|<span data-ttu-id="40a96-116">Popis</span><span class="sxs-lookup"><span data-stu-id="40a96-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="40a96-117">Určuje přihlašovací údaje pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="40a96-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="40a96-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="40a96-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="40a96-119">Určuje přihlašovací údaje pro ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="40a96-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="40a96-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="40a96-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="40a96-121">Řetězec určující sféru ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="40a96-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="40a96-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="40a96-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="40a96-123">Sféra ověření určuje nejméně název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="40a96-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="40a96-124">Můžete také určit kolekci uživatelů, který má přístup.</span><span class="sxs-lookup"><span data-stu-id="40a96-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="40a96-125">Sféra ověření pro ověření, který z nich několik možných uživatelská jména a hesla je možné dotazovat uživatele.</span><span class="sxs-lookup"><span data-stu-id="40a96-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="40a96-126">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="40a96-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="40a96-127">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="40a96-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="40a96-128">2.  WhenSupported – zásady se vynucuje jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="40a96-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="40a96-129">3.  Vždy – je vždy zásady vynucují.</span><span class="sxs-lookup"><span data-stu-id="40a96-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="40a96-130">K ověření se nezdaří klientů, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="40a96-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="40a96-131">clientCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="40a96-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="40a96-132">Value</span><span class="sxs-lookup"><span data-stu-id="40a96-132">Value</span></span>|<span data-ttu-id="40a96-133">Popis</span><span class="sxs-lookup"><span data-stu-id="40a96-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="40a96-134">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="40a96-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="40a96-135">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="40a96-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="40a96-136">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="40a96-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="40a96-137">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="40a96-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="40a96-138">Ověřování protokolem NTLM se používá jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="40a96-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="40a96-139">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="40a96-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="40a96-140">proxyCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="40a96-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="40a96-141">Value</span><span class="sxs-lookup"><span data-stu-id="40a96-141">Value</span></span>|<span data-ttu-id="40a96-142">Popis</span><span class="sxs-lookup"><span data-stu-id="40a96-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="40a96-143">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="40a96-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="40a96-144">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="40a96-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="40a96-145">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="40a96-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="40a96-146">Používá NTLM jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="40a96-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="40a96-147">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="40a96-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40a96-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="40a96-148">Child Elements</span></span>  
 <span data-ttu-id="40a96-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="40a96-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40a96-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="40a96-150">Parent Elements</span></span>  
  
|<span data-ttu-id="40a96-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="40a96-151">Element</span></span>|<span data-ttu-id="40a96-152">Popis</span><span class="sxs-lookup"><span data-stu-id="40a96-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40a96-153">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="40a96-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="40a96-154">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="40a96-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40a96-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40a96-155">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="40a96-156">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="40a96-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="40a96-157">Vazby</span><span class="sxs-lookup"><span data-stu-id="40a96-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="40a96-158">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="40a96-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="40a96-159">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="40a96-159">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="40a96-160">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="40a96-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="40a96-161">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="40a96-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
