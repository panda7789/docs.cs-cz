---
title: <transport> z <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: f78add5397644dc40bfd22f10bd84aa5c5eb29e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923213"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="5c78e-102">\<> přenosu > \<WebHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5c78e-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="5c78e-103">Definuje nastavení zabezpečení na úrovni přenosu pro koncový bod služby nakonfigurovanou pro příjem požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="5c78e-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="5c78e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5c78e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5c78e-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="5c78e-105">\<bindings></span></span>  
<span data-ttu-id="5c78e-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5c78e-106">\<webHttpBinding></span></span>  
<span data-ttu-id="5c78e-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="5c78e-107">\<binding></span></span>  
<span data-ttu-id="5c78e-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5c78e-108">\<security></span></span>  
<span data-ttu-id="5c78e-109">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="5c78e-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c78e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c78e-110">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="5c78e-111">type</span><span class="sxs-lookup"><span data-stu-id="5c78e-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c78e-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5c78e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5c78e-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5c78e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c78e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5c78e-114">Attributes</span></span>  
  
|<span data-ttu-id="5c78e-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="5c78e-115">Attribute</span></span>|<span data-ttu-id="5c78e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5c78e-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="5c78e-117">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="5c78e-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="5c78e-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5c78e-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="5c78e-119">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="5c78e-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="5c78e-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5c78e-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="5c78e-121">Řetězec, který určuje sféru ověřování pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="5c78e-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="5c78e-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5c78e-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="5c78e-123">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="5c78e-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="5c78e-124">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="5c78e-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="5c78e-125">Uživatel může zadat dotaz na sféru ověření, aby bylo možné zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="5c78e-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="5c78e-126">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> se má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="5c78e-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="5c78e-127">1.  Nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="5c78e-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="5c78e-128">2.  WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="5c78e-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="5c78e-129">3.  Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="5c78e-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="5c78e-130">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="5c78e-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5c78e-131">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="5c78e-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5c78e-132">Value</span><span class="sxs-lookup"><span data-stu-id="5c78e-132">Value</span></span>|<span data-ttu-id="5c78e-133">Popis</span><span class="sxs-lookup"><span data-stu-id="5c78e-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="5c78e-134">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="5c78e-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="5c78e-135">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="5c78e-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="5c78e-136">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="5c78e-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="5c78e-137">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="5c78e-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="5c78e-138">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5c78e-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="5c78e-139">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5c78e-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="5c78e-140">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="5c78e-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5c78e-141">Value</span><span class="sxs-lookup"><span data-stu-id="5c78e-141">Value</span></span>|<span data-ttu-id="5c78e-142">Popis</span><span class="sxs-lookup"><span data-stu-id="5c78e-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="5c78e-143">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="5c78e-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="5c78e-144">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="5c78e-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="5c78e-145">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="5c78e-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="5c78e-146">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5c78e-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="5c78e-147">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5c78e-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c78e-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5c78e-148">Child Elements</span></span>  
 <span data-ttu-id="5c78e-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c78e-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c78e-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5c78e-150">Parent Elements</span></span>  
  
|<span data-ttu-id="5c78e-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="5c78e-151">Element</span></span>|<span data-ttu-id="5c78e-152">Popis</span><span class="sxs-lookup"><span data-stu-id="5c78e-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c78e-153">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5c78e-153">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="5c78e-154">Představuje možnosti [ \<zabezpečení elementu WSHttpBinding >](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="5c78e-154">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c78e-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c78e-155">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="5c78e-156">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5c78e-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5c78e-157">Vazby</span><span class="sxs-lookup"><span data-stu-id="5c78e-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5c78e-158">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5c78e-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5c78e-159">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5c78e-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5c78e-160">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="5c78e-160">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="5c78e-161">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="5c78e-161">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
