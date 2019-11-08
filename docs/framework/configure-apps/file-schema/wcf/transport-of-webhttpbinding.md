---
title: <transport> z <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732788"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="16bd6-102">> \<přenosů \<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="16bd6-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="16bd6-103">Definuje nastavení zabezpečení na úrovni přenosu pro koncový bod služby nakonfigurovanou pro příjem požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="16bd6-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
<span data-ttu-id="16bd6-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="16bd6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="16bd6-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="16bd6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="16bd6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="16bd6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="16bd6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<webHttpBinding >** ](webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="16bd6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)</span></span>\
<span data-ttu-id="16bd6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="16bd6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="16bd6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-webhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="16bd6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)</span></span>\
<span data-ttu-id="16bd6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**</span><span class="sxs-lookup"><span data-stu-id="16bd6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16bd6-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16bd6-111">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="16bd6-112">Typ</span><span class="sxs-lookup"><span data-stu-id="16bd6-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16bd6-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="16bd6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="16bd6-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="16bd6-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16bd6-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="16bd6-115">Attributes</span></span>  
  
|<span data-ttu-id="16bd6-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="16bd6-116">Attribute</span></span>|<span data-ttu-id="16bd6-117">Popis</span><span class="sxs-lookup"><span data-stu-id="16bd6-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="16bd6-118">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="16bd6-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="16bd6-119">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="16bd6-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="16bd6-120">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="16bd6-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="16bd6-121">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="16bd6-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="16bd6-122">Řetězec, který určuje sféru ověřování pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="16bd6-122">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="16bd6-123">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="16bd6-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="16bd6-124">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="16bd6-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="16bd6-125">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="16bd6-125">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="16bd6-126">Uživatel může zadat dotaz na sféru ověření, aby bylo možné zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="16bd6-126">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="16bd6-127">Tento výčet Určuje, kdy se má vyhovět <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.</span><span class="sxs-lookup"><span data-stu-id="16bd6-127">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="16bd6-128">1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="16bd6-128">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="16bd6-129">2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="16bd6-129">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="16bd6-130">3. Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="16bd6-130">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="16bd6-131">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="16bd6-131">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="16bd6-132">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="16bd6-132">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="16bd6-133">Hodnota</span><span class="sxs-lookup"><span data-stu-id="16bd6-133">Value</span></span>|<span data-ttu-id="16bd6-134">Popis</span><span class="sxs-lookup"><span data-stu-id="16bd6-134">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="16bd6-135">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="16bd6-135">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="16bd6-136">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="16bd6-136">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="16bd6-137">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="16bd6-137">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="16bd6-138">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="16bd6-138">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="16bd6-139">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="16bd6-139">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="16bd6-140">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="16bd6-140">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="16bd6-141">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="16bd6-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="16bd6-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="16bd6-142">Value</span></span>|<span data-ttu-id="16bd6-143">Popis</span><span class="sxs-lookup"><span data-stu-id="16bd6-143">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="16bd6-144">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="16bd6-144">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="16bd6-145">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="16bd6-145">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="16bd6-146">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="16bd6-146">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="16bd6-147">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="16bd6-147">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="16bd6-148">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="16bd6-148">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16bd6-149">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="16bd6-149">Child Elements</span></span>  
 <span data-ttu-id="16bd6-150">Žádné</span><span class="sxs-lookup"><span data-stu-id="16bd6-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16bd6-151">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="16bd6-151">Parent Elements</span></span>  
  
|<span data-ttu-id="16bd6-152">Prvek</span><span class="sxs-lookup"><span data-stu-id="16bd6-152">Element</span></span>|<span data-ttu-id="16bd6-153">Popis</span><span class="sxs-lookup"><span data-stu-id="16bd6-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16bd6-154">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="16bd6-154">\<security></span></span>](security-of-webhttpbinding.md)|<span data-ttu-id="16bd6-155">Představuje možnosti zabezpečení [\<wsHttpBinding >](wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="16bd6-155">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16bd6-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16bd6-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="16bd6-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="16bd6-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="16bd6-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="16bd6-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="16bd6-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="16bd6-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="16bd6-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="16bd6-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="16bd6-161">vazba \<</span><span class="sxs-lookup"><span data-stu-id="16bd6-161">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="16bd6-162">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="16bd6-162">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
