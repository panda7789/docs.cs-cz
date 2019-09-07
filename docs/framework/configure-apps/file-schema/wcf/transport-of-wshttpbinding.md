---
title: <transport> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 95cfa076f62f767af431ff5a0bcc2ca31b824e30
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399246"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="c29a7-102">\<> přenosu > \<WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c29a7-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="c29a7-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="c29a7-103">Defines authentication settings for the HTTP transport.</span></span>

<span data-ttu-id="c29a7-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c29a7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c29a7-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c29a7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c29a7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c29a7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c29a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c29a7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="c29a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="c29a7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c29a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c29a7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)</span></span>\
<span data-ttu-id="c29a7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> přenosu**</span><span class="sxs-lookup"><span data-stu-id="c29a7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="c29a7-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c29a7-111">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="c29a7-112">type</span><span class="sxs-lookup"><span data-stu-id="c29a7-112">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="c29a7-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c29a7-113">Attributes and Elements</span></span>

<span data-ttu-id="c29a7-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c29a7-114">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c29a7-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="c29a7-115">Attributes</span></span>

|<span data-ttu-id="c29a7-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="c29a7-116">Attribute</span></span>|<span data-ttu-id="c29a7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c29a7-117">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="c29a7-118">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="c29a7-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="c29a7-119">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="c29a7-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="c29a7-120">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="c29a7-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="c29a7-121">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="c29a7-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="c29a7-122">Řetězec, který určuje sféru ověřování pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="c29a7-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="c29a7-123">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c29a7-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="c29a7-124">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="c29a7-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="c29a7-125">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="c29a7-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="c29a7-126">Uživatel může zadat dotaz na sféru ověření, aby bylo možné zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="c29a7-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="c29a7-127">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> se má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="c29a7-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="c29a7-128">1.  Nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="c29a7-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="c29a7-129">2.  WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="c29a7-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="c29a7-130">3.  Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="c29a7-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="c29a7-131">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="c29a7-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="c29a7-132">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="c29a7-132">clientCredentialType Attribute</span></span>

|<span data-ttu-id="c29a7-133">Value</span><span class="sxs-lookup"><span data-stu-id="c29a7-133">Value</span></span>|<span data-ttu-id="c29a7-134">Popis</span><span class="sxs-lookup"><span data-stu-id="c29a7-134">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="c29a7-135">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="c29a7-135">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="c29a7-136">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="c29a7-136">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="c29a7-137">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="c29a7-137">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="c29a7-138">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c29a7-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="c29a7-139">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c29a7-139">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="c29a7-140">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="c29a7-140">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="c29a7-141">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="c29a7-141">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="c29a7-142">Value</span><span class="sxs-lookup"><span data-stu-id="c29a7-142">Value</span></span>|<span data-ttu-id="c29a7-143">Popis</span><span class="sxs-lookup"><span data-stu-id="c29a7-143">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="c29a7-144">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="c29a7-144">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="c29a7-145">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="c29a7-145">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="c29a7-146">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="c29a7-146">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="c29a7-147">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c29a7-147">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="c29a7-148">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c29a7-148">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="c29a7-149">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="c29a7-149">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c29a7-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c29a7-150">Child Elements</span></span>

<span data-ttu-id="c29a7-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="c29a7-151">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c29a7-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c29a7-152">Parent Elements</span></span>

|<span data-ttu-id="c29a7-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="c29a7-153">Element</span></span>|<span data-ttu-id="c29a7-154">Popis</span><span class="sxs-lookup"><span data-stu-id="c29a7-154">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c29a7-155">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c29a7-155">\<security></span></span>](security-of-wshttpbinding.md)|<span data-ttu-id="c29a7-156">Představuje možnosti [ \<zabezpečení wsHttpBinding >](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c29a7-156">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="c29a7-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c29a7-157">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="c29a7-158">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c29a7-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c29a7-159">Vazby</span><span class="sxs-lookup"><span data-stu-id="c29a7-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c29a7-160">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="c29a7-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c29a7-161">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c29a7-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c29a7-162">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="c29a7-162">\<binding></span></span>](../../../misc/binding.md)
