---
title: <transport> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732734"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="6b21e-102">> \<přenosů \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6b21e-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="6b21e-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="6b21e-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="6b21e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6b21e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b21e-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6b21e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6b21e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6b21e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6b21e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6b21e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="6b21e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="6b21e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6b21e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6b21e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)</span></span>\
<span data-ttu-id="6b21e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**</span><span class="sxs-lookup"><span data-stu-id="6b21e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="6b21e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b21e-111">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="6b21e-112">Typ</span><span class="sxs-lookup"><span data-stu-id="6b21e-112">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="6b21e-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6b21e-113">Attributes and Elements</span></span>

<span data-ttu-id="6b21e-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6b21e-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b21e-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="6b21e-115">Attributes</span></span>

|<span data-ttu-id="6b21e-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b21e-116">Attribute</span></span>|<span data-ttu-id="6b21e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6b21e-117">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="6b21e-118">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="6b21e-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="6b21e-119">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="6b21e-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="6b21e-120">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="6b21e-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="6b21e-121">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="6b21e-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="6b21e-122">Řetězec, který určuje sféru ověřování pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="6b21e-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="6b21e-123">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="6b21e-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="6b21e-124">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="6b21e-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="6b21e-125">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="6b21e-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="6b21e-126">Uživatel může zadat dotaz na sféru ověření, aby bylo možné zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="6b21e-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="6b21e-127">Tento výčet Určuje, kdy se má vyhovět <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.</span><span class="sxs-lookup"><span data-stu-id="6b21e-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="6b21e-128">1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="6b21e-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="6b21e-129">2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="6b21e-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="6b21e-130">3. Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="6b21e-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="6b21e-131">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="6b21e-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="6b21e-132">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="6b21e-132">clientCredentialType Attribute</span></span>

|<span data-ttu-id="6b21e-133">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6b21e-133">Value</span></span>|<span data-ttu-id="6b21e-134">Popis</span><span class="sxs-lookup"><span data-stu-id="6b21e-134">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="6b21e-135">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="6b21e-135">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="6b21e-136">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="6b21e-136">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="6b21e-137">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="6b21e-137">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="6b21e-138">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6b21e-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="6b21e-139">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6b21e-139">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="6b21e-140">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="6b21e-140">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="6b21e-141">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="6b21e-141">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="6b21e-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6b21e-142">Value</span></span>|<span data-ttu-id="6b21e-143">Popis</span><span class="sxs-lookup"><span data-stu-id="6b21e-143">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="6b21e-144">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="6b21e-144">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="6b21e-145">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="6b21e-145">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="6b21e-146">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="6b21e-146">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="6b21e-147">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6b21e-147">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="6b21e-148">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6b21e-148">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="6b21e-149">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="6b21e-149">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6b21e-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6b21e-150">Child Elements</span></span>

<span data-ttu-id="6b21e-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="6b21e-151">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6b21e-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6b21e-152">Parent Elements</span></span>

|<span data-ttu-id="6b21e-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="6b21e-153">Element</span></span>|<span data-ttu-id="6b21e-154">Popis</span><span class="sxs-lookup"><span data-stu-id="6b21e-154">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b21e-155">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="6b21e-155">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="6b21e-156">Představuje možnosti zabezpečení [\<wsHttpBinding >](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6b21e-156">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="6b21e-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b21e-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="6b21e-158">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6b21e-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6b21e-159">Vazby</span><span class="sxs-lookup"><span data-stu-id="6b21e-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6b21e-160">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="6b21e-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6b21e-161">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6b21e-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6b21e-162">vazba \<</span><span class="sxs-lookup"><span data-stu-id="6b21e-162">\<binding></span></span>](bindings.md)
