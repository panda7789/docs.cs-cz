---
title: <transport> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: b8f84d0ed6c6248e72e3353675c9da96a0678ae6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273303"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="07e8e-102">\<přenos > z \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="07e8e-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="07e8e-103">Definuje nastavení ověřování pro přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="07e8e-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="07e8e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="07e8e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="07e8e-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="07e8e-105">\<bindings></span></span>  
<span data-ttu-id="07e8e-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="07e8e-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="07e8e-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="07e8e-107">\<binding></span></span>  
<span data-ttu-id="07e8e-108">\<security></span><span class="sxs-lookup"><span data-stu-id="07e8e-108">\<security></span></span>  
<span data-ttu-id="07e8e-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="07e8e-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e8e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07e8e-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="07e8e-111">Typ</span><span class="sxs-lookup"><span data-stu-id="07e8e-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07e8e-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="07e8e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="07e8e-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="07e8e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07e8e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="07e8e-114">Attributes</span></span>  
  
|<span data-ttu-id="07e8e-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="07e8e-115">Attribute</span></span>|<span data-ttu-id="07e8e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="07e8e-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="07e8e-117">Určuje přihlašovací údaje pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="07e8e-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="07e8e-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="07e8e-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="07e8e-119">Určuje přihlašovací údaje pro ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="07e8e-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="07e8e-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="07e8e-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="07e8e-121">Sféra ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="07e8e-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="07e8e-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="07e8e-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="07e8e-123">Sféra ověření určuje nejméně název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="07e8e-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="07e8e-124">Můžete také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="07e8e-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="07e8e-125">Sféra ověření k určení, která z nich několik možných uživatelská jména a hesla je možné dotazovat uživatele.</span><span class="sxs-lookup"><span data-stu-id="07e8e-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="07e8e-126">clientCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="07e8e-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="07e8e-127">Hodnota</span><span class="sxs-lookup"><span data-stu-id="07e8e-127">Value</span></span>|<span data-ttu-id="07e8e-128">Popis</span><span class="sxs-lookup"><span data-stu-id="07e8e-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07e8e-129">Žádná</span><span class="sxs-lookup"><span data-stu-id="07e8e-129">None</span></span>|<span data-ttu-id="07e8e-130">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="07e8e-130">Security is disabled.</span></span>|  
|<span data-ttu-id="07e8e-131">Základní</span><span class="sxs-lookup"><span data-stu-id="07e8e-131">Basic</span></span>|<span data-ttu-id="07e8e-132">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="07e8e-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="07e8e-133">ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="07e8e-133">Digest</span></span>|<span data-ttu-id="07e8e-134">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="07e8e-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="07e8e-135">Ntlm</span><span class="sxs-lookup"><span data-stu-id="07e8e-135">Ntlm</span></span>|<span data-ttu-id="07e8e-136">Ověřování protokolem NTLM se používá jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="07e8e-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="07e8e-137">Windows</span><span class="sxs-lookup"><span data-stu-id="07e8e-137">Windows</span></span>|<span data-ttu-id="07e8e-138">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="07e8e-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="07e8e-139">Certifikát</span><span class="sxs-lookup"><span data-stu-id="07e8e-139">Certificate</span></span>|<span data-ttu-id="07e8e-140">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="07e8e-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="07e8e-141">proxyCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="07e8e-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="07e8e-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="07e8e-142">Value</span></span>|<span data-ttu-id="07e8e-143">Popis</span><span class="sxs-lookup"><span data-stu-id="07e8e-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="07e8e-144">Žádná</span><span class="sxs-lookup"><span data-stu-id="07e8e-144">None</span></span>|<span data-ttu-id="07e8e-145">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="07e8e-145">Security is disabled.</span></span>|  
|<span data-ttu-id="07e8e-146">Základní</span><span class="sxs-lookup"><span data-stu-id="07e8e-146">Basic</span></span>|<span data-ttu-id="07e8e-147">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="07e8e-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="07e8e-148">ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="07e8e-148">Digest</span></span>|<span data-ttu-id="07e8e-149">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="07e8e-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="07e8e-150">Ntlm</span><span class="sxs-lookup"><span data-stu-id="07e8e-150">Ntlm</span></span>|<span data-ttu-id="07e8e-151">Používá NTLM jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="07e8e-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="07e8e-152">Windows</span><span class="sxs-lookup"><span data-stu-id="07e8e-152">Windows</span></span>|<span data-ttu-id="07e8e-153">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="07e8e-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="07e8e-154">Certifikát</span><span class="sxs-lookup"><span data-stu-id="07e8e-154">Certificate</span></span>|<span data-ttu-id="07e8e-155">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="07e8e-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07e8e-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="07e8e-156">Child Elements</span></span>  
 <span data-ttu-id="07e8e-157">Žádná</span><span class="sxs-lookup"><span data-stu-id="07e8e-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07e8e-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="07e8e-158">Parent Elements</span></span>  
  
|<span data-ttu-id="07e8e-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="07e8e-159">Element</span></span>|<span data-ttu-id="07e8e-160">Popis</span><span class="sxs-lookup"><span data-stu-id="07e8e-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07e8e-161">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="07e8e-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="07e8e-162">Představuje možnosti zabezpečení [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="07e8e-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07e8e-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07e8e-163">See also</span></span>
- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="07e8e-164">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="07e8e-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="07e8e-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="07e8e-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="07e8e-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="07e8e-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="07e8e-167">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="07e8e-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="07e8e-168">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="07e8e-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
