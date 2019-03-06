---
title: <transport> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: ea025751020d6d98292f6bc3ecfe9421af0cb793
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372318"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="15178-102">\<přenos > z \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="15178-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="15178-103">Definuje nastavení ověřování pro přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="15178-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="15178-104">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="15178-104">\<system.serviceModel>\\</span></span>
<span data-ttu-id="15178-105">\<vazby > \\</span><span class="sxs-lookup"><span data-stu-id="15178-105">\<bindings>\\</span></span>
<span data-ttu-id="15178-106">\<wsHttpBinding>\\</span><span class="sxs-lookup"><span data-stu-id="15178-106">\<wsHttpBinding>\\</span></span>
<span data-ttu-id="15178-107">\<binding>\\</span><span class="sxs-lookup"><span data-stu-id="15178-107">\<binding>\\</span></span>
<span data-ttu-id="15178-108">\<security>\\</span><span class="sxs-lookup"><span data-stu-id="15178-108">\<security>\\</span></span>
<span data-ttu-id="15178-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="15178-109">\<transport></span></span>

## <a name="syntax"></a><span data-ttu-id="15178-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15178-110">Syntax</span></span>

```xml
<wsHttpBinding>
  <binding>
    <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"
                 proxyCredentialType="Basic|Digest|None|Ntlm|Windows"
                 realm="string" />
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</wsHttpBinding>
```

## <a name="type"></a><span data-ttu-id="15178-111">Typ</span><span class="sxs-lookup"><span data-stu-id="15178-111">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="15178-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="15178-112">Attributes and Elements</span></span>

<span data-ttu-id="15178-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="15178-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="15178-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="15178-114">Attributes</span></span>

|<span data-ttu-id="15178-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="15178-115">Attribute</span></span>|<span data-ttu-id="15178-116">Popis</span><span class="sxs-lookup"><span data-stu-id="15178-116">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="15178-117">Určuje přihlašovací údaje pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="15178-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="15178-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="15178-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="15178-119">Určuje přihlašovací údaje pro ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="15178-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="15178-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="15178-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="15178-121">Řetězec určující sféru ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="15178-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="15178-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="15178-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="15178-123">Sféra ověření určuje nejméně název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="15178-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="15178-124">Můžete také určit kolekci uživatelů, který má přístup.</span><span class="sxs-lookup"><span data-stu-id="15178-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="15178-125">Sféra ověření pro ověření, který z nich několik možných uživatelská jména a hesla je možné dotazovat uživatele.</span><span class="sxs-lookup"><span data-stu-id="15178-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="15178-126">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="15178-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="15178-127">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="15178-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="15178-128">2.  WhenSupported – zásady se vynucuje jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="15178-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="15178-129">3.  Vždy – je vždy zásady vynucují.</span><span class="sxs-lookup"><span data-stu-id="15178-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="15178-130">K ověření se nezdaří klientů, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="15178-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="15178-131">clientCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="15178-131">clientCredentialType Attribute</span></span>

|<span data-ttu-id="15178-132">Hodnota</span><span class="sxs-lookup"><span data-stu-id="15178-132">Value</span></span>|<span data-ttu-id="15178-133">Popis</span><span class="sxs-lookup"><span data-stu-id="15178-133">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="15178-134">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="15178-134">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="15178-135">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="15178-135">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="15178-136">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="15178-136">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="15178-137">Ověřování protokolem NTLM se používá jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="15178-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="15178-138">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="15178-138">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="15178-139">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="15178-139">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="15178-140">proxyCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="15178-140">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="15178-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="15178-141">Value</span></span>|<span data-ttu-id="15178-142">Popis</span><span class="sxs-lookup"><span data-stu-id="15178-142">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="15178-143">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="15178-143">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="15178-144">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="15178-144">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="15178-145">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="15178-145">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="15178-146">Používá NTLM jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="15178-146">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="15178-147">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="15178-147">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="15178-148">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="15178-148">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="15178-149">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="15178-149">Child Elements</span></span>

<span data-ttu-id="15178-150">Žádné</span><span class="sxs-lookup"><span data-stu-id="15178-150">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="15178-151">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="15178-151">Parent Elements</span></span>

|<span data-ttu-id="15178-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="15178-152">Element</span></span>|<span data-ttu-id="15178-153">Popis</span><span class="sxs-lookup"><span data-stu-id="15178-153">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="15178-154">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="15178-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="15178-155">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="15178-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="15178-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15178-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="15178-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="15178-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="15178-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="15178-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="15178-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="15178-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="15178-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="15178-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="15178-161">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="15178-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
