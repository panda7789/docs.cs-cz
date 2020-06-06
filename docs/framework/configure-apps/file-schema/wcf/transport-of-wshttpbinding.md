---
title: <transport> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
ms.openlocfilehash: 1afeed62fcbf3b083d69a7cedb7eb80b81f5c17b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732734"
---
# <a name="transport-of-wshttpbinding"></a><span data-ttu-id="4da16-102">\<transport> z \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4da16-102">\<transport> of \<wsHttpBinding></span></span>

<span data-ttu-id="4da16-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="4da16-103">Defines authentication settings for the HTTP transport.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  

## <a name="syntax"></a><span data-ttu-id="4da16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4da16-104">Syntax</span></span>

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

## <a name="type"></a><span data-ttu-id="4da16-105">Typ</span><span class="sxs-lookup"><span data-stu-id="4da16-105">Type</span></span>

<xref:System.ServiceModel.HttpTransportSecurity>

## <a name="attributes-and-elements"></a><span data-ttu-id="4da16-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4da16-106">Attributes and Elements</span></span>

<span data-ttu-id="4da16-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4da16-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4da16-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="4da16-108">Attributes</span></span>

|<span data-ttu-id="4da16-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="4da16-109">Attribute</span></span>|<span data-ttu-id="4da16-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4da16-110">Description</span></span>|
|---------------|-----------------|
|`clientCredentialType`|<span data-ttu-id="4da16-111">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="4da16-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="4da16-112">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="4da16-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|
|`proxyCredentialType`|<span data-ttu-id="4da16-113">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="4da16-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="4da16-114">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="4da16-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|
|`realm`|<span data-ttu-id="4da16-115">Řetězec, který určuje sféru ověřování pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="4da16-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="4da16-116">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="4da16-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="4da16-117">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="4da16-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="4da16-118">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="4da16-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="4da16-119">Uživatel může zadat dotaz na sféru ověření, aby bylo možné zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="4da16-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|
|`policyEnforcement`|<span data-ttu-id="4da16-120">Tento výčet Určuje, kdy se <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="4da16-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="4da16-121">1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="4da16-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="4da16-122">2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="4da16-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="4da16-123">3. Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="4da16-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="4da16-124">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="4da16-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|

## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="4da16-125">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="4da16-125">clientCredentialType Attribute</span></span>

|<span data-ttu-id="4da16-126">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4da16-126">Value</span></span>|<span data-ttu-id="4da16-127">Description</span><span class="sxs-lookup"><span data-stu-id="4da16-127">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="4da16-128">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="4da16-128">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="4da16-129">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="4da16-129">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="4da16-130">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="4da16-130">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="4da16-131">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4da16-131">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="4da16-132">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4da16-132">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="4da16-133">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="4da16-133">Uses X.509 certificates to authenticate the client.</span></span>|

## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="4da16-134">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="4da16-134">proxyCredentialType Attribute</span></span>

|<span data-ttu-id="4da16-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="4da16-135">Value</span></span>|<span data-ttu-id="4da16-136">Description</span><span class="sxs-lookup"><span data-stu-id="4da16-136">Description</span></span>|
|-----------|-----------------|
|`None`|<span data-ttu-id="4da16-137">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="4da16-137">Security is disabled.</span></span>|
|`Basic`|<span data-ttu-id="4da16-138">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="4da16-138">Uses basic authentication.</span></span>|
|`Digest`|<span data-ttu-id="4da16-139">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="4da16-139">Uses digest authentication.</span></span>|
|`Ntlm`|<span data-ttu-id="4da16-140">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4da16-140">Uses NTLM as a fallback with a Windows domain.</span></span>|
|`Windows`|<span data-ttu-id="4da16-141">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="4da16-141">Uses integrated Windows authentication.</span></span>|
|`Certificate`|<span data-ttu-id="4da16-142">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="4da16-142">Uses X.509 certificates to authenticate the client.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4da16-143">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4da16-143">Child Elements</span></span>

<span data-ttu-id="4da16-144">Žádné</span><span class="sxs-lookup"><span data-stu-id="4da16-144">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4da16-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4da16-145">Parent Elements</span></span>

|<span data-ttu-id="4da16-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="4da16-146">Element</span></span>|<span data-ttu-id="4da16-147">Description</span><span class="sxs-lookup"><span data-stu-id="4da16-147">Description</span></span>|
|-------------|-----------------|
|[\<security>](security-of-wshttpbinding.md)|<span data-ttu-id="4da16-148">Představuje možnosti zabezpečení [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4da16-148">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>|

## <a name="see-also"></a><span data-ttu-id="4da16-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="4da16-149">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="4da16-150">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4da16-150">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4da16-151">Vazby</span><span class="sxs-lookup"><span data-stu-id="4da16-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4da16-152">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="4da16-152">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4da16-153">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4da16-153">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
