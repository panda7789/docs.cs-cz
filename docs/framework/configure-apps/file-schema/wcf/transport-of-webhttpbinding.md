---
title: <transport> z <webHttpBinding>
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: e8016eb9058f132722587368f1f8c7c03220af4a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732788"
---
# <a name="transport-of-webhttpbinding"></a><span data-ttu-id="5873f-102">\<transport> z \<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5873f-102">\<transport> of \<webHttpBinding></span></span>
<span data-ttu-id="5873f-103">Definuje nastavení zabezpečení na úrovni přenosu pro koncový bod služby nakonfigurovanou pro příjem požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="5873f-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<webHttpBinding>**](webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-webhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="5873f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5873f-104">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="5873f-105">Typ</span><span class="sxs-lookup"><span data-stu-id="5873f-105">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5873f-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5873f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5873f-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5873f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5873f-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="5873f-108">Attributes</span></span>  
  
|<span data-ttu-id="5873f-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="5873f-109">Attribute</span></span>|<span data-ttu-id="5873f-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5873f-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="5873f-111">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="5873f-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="5873f-112">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="5873f-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="5873f-113">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="5873f-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="5873f-114">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="5873f-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="5873f-115">Řetězec, který určuje sféru ověřování pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="5873f-115">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="5873f-116">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5873f-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="5873f-117">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="5873f-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="5873f-118">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="5873f-118">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="5873f-119">Uživatel může zadat dotaz na sféru ověření, aby bylo možné zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="5873f-119">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="5873f-120">Tento výčet Určuje, kdy se <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="5873f-120">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="5873f-121">1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="5873f-121">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="5873f-122">2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="5873f-122">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="5873f-123">3. Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="5873f-123">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="5873f-124">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="5873f-124">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5873f-125">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="5873f-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5873f-126">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5873f-126">Value</span></span>|<span data-ttu-id="5873f-127">Description</span><span class="sxs-lookup"><span data-stu-id="5873f-127">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="5873f-128">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="5873f-128">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="5873f-129">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="5873f-129">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="5873f-130">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="5873f-130">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="5873f-131">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="5873f-131">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="5873f-132">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5873f-132">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="5873f-133">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5873f-133">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="5873f-134">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="5873f-134">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5873f-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5873f-135">Value</span></span>|<span data-ttu-id="5873f-136">Description</span><span class="sxs-lookup"><span data-stu-id="5873f-136">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="5873f-137">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="5873f-137">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="5873f-138">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="5873f-138">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="5873f-139">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="5873f-139">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="5873f-140">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5873f-140">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="5873f-141">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5873f-141">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5873f-142">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5873f-142">Child Elements</span></span>  
 <span data-ttu-id="5873f-143">Žádné</span><span class="sxs-lookup"><span data-stu-id="5873f-143">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5873f-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5873f-144">Parent Elements</span></span>  
  
|<span data-ttu-id="5873f-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="5873f-145">Element</span></span>|<span data-ttu-id="5873f-146">Description</span><span class="sxs-lookup"><span data-stu-id="5873f-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-webhttpbinding.md)|<span data-ttu-id="5873f-147">Představuje možnosti zabezpečení [\<wsHttpBinding>](wshttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="5873f-147">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5873f-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="5873f-148">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- [<span data-ttu-id="5873f-149">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5873f-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5873f-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="5873f-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5873f-151">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5873f-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5873f-152">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5873f-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="5873f-153">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="5873f-153">WCF Web HTTP Programming Model</span></span>](../../../wcf/feature-details/wcf-web-http-programming-model.md)
