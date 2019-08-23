---
title: <transport> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 384267e3d018d714f95356461eb303bc9ec0cb3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934640"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="056e2-102">\<> přenosu > \<WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="056e2-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="056e2-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="056e2-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="056e2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="056e2-104">\<system.serviceModel></span></span>\
<span data-ttu-id="056e2-105">\<vazby > </span><span class="sxs-lookup"><span data-stu-id="056e2-105">\<bindings></span></span>\
<span data-ttu-id="056e2-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="056e2-106">\<wsHttpBinding></span></span>\
<span data-ttu-id="056e2-107">\<> vazby </span><span class="sxs-lookup"><span data-stu-id="056e2-107">\<binding></span></span>\
<span data-ttu-id="056e2-108">\<> zabezpečení </span><span class="sxs-lookup"><span data-stu-id="056e2-108">\<security></span></span>\
<span data-ttu-id="056e2-109">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="056e2-109">\<transport></span></span>

## <a name="syntax"></a><span data-ttu-id="056e2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="056e2-110">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="056e2-111">type</span><span class="sxs-lookup"><span data-stu-id="056e2-111">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="056e2-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="056e2-112">Attributes and Elements</span></span>

<span data-ttu-id="056e2-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="056e2-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="056e2-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="056e2-114">Attributes</span></span>

|<span data-ttu-id="056e2-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="056e2-115">Attribute</span></span>|<span data-ttu-id="056e2-116">Popis</span><span class="sxs-lookup"><span data-stu-id="056e2-116">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="056e2-117">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="056e2-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="056e2-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="056e2-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="056e2-119">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="056e2-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="056e2-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="056e2-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="056e2-121">Řetězec, který určuje sféru ověřování pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="056e2-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="056e2-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="056e2-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="056e2-123">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="056e2-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="056e2-124">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="056e2-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="056e2-125">Uživatel může zadat dotaz na sféru ověření, aby bylo možné zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="056e2-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="056e2-126">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> se má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="056e2-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="056e2-127">1.  Nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="056e2-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="056e2-128">2.  WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="056e2-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="056e2-129">3.  Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="056e2-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="056e2-130">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="056e2-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="056e2-131">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="056e2-131">clientCredentialType Attribute</span></span>

|<span data-ttu-id="056e2-132">Value</span><span class="sxs-lookup"><span data-stu-id="056e2-132">Value</span></span>|<span data-ttu-id="056e2-133">Popis</span><span class="sxs-lookup"><span data-stu-id="056e2-133">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="056e2-134">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="056e2-134">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="056e2-135">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="056e2-135">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="056e2-136">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="056e2-136">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="056e2-137">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="056e2-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="056e2-138">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="056e2-138">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="056e2-139">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="056e2-139">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="056e2-140">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="056e2-140">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="056e2-141">Value</span><span class="sxs-lookup"><span data-stu-id="056e2-141">Value</span></span>|<span data-ttu-id="056e2-142">Popis</span><span class="sxs-lookup"><span data-stu-id="056e2-142">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="056e2-143">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="056e2-143">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="056e2-144">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="056e2-144">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="056e2-145">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="056e2-145">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="056e2-146">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="056e2-146">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="056e2-147">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="056e2-147">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="056e2-148">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="056e2-148">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="056e2-149">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="056e2-149">Child Elements</span></span>

<span data-ttu-id="056e2-150">Žádné</span><span class="sxs-lookup"><span data-stu-id="056e2-150">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="056e2-151">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="056e2-151">Parent Elements</span></span>

|<span data-ttu-id="056e2-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="056e2-152">Element</span></span>|<span data-ttu-id="056e2-153">Popis</span><span class="sxs-lookup"><span data-stu-id="056e2-153">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="056e2-154">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="056e2-154">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="056e2-155">Představuje možnosti [ \<zabezpečení wsHttpBinding >](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="056e2-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="056e2-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="056e2-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="056e2-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="056e2-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="056e2-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="056e2-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="056e2-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="056e2-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="056e2-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="056e2-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="056e2-161">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="056e2-161">\<binding></span></span>](../../../misc/binding.md)
