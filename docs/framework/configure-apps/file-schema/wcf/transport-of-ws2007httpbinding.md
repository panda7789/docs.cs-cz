---
title: <transport> of <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: a1540b53d4af76141c1daee60a6bddbbecd9d6da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153865"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="72554-102">\<přenos > z \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="72554-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="72554-103">Definuje nastavení ověřování pro přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="72554-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="72554-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="72554-104">\<system.serviceModel></span></span>  
<span data-ttu-id="72554-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="72554-105">\<bindings></span></span>  
<span data-ttu-id="72554-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="72554-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="72554-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="72554-107">\<binding></span></span>  
<span data-ttu-id="72554-108">\<security></span><span class="sxs-lookup"><span data-stu-id="72554-108">\<security></span></span>  
<span data-ttu-id="72554-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="72554-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72554-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72554-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="72554-111">Type</span><span class="sxs-lookup"><span data-stu-id="72554-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72554-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="72554-112">Attributes and Elements</span></span>  
 <span data-ttu-id="72554-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="72554-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72554-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="72554-114">Attributes</span></span>  
  
|<span data-ttu-id="72554-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="72554-115">Attribute</span></span>|<span data-ttu-id="72554-116">Popis</span><span class="sxs-lookup"><span data-stu-id="72554-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="72554-117">Určuje přihlašovací údaje pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="72554-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="72554-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="72554-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="72554-119">Určuje přihlašovací údaje pro ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="72554-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="72554-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="72554-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="72554-121">Sféra ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="72554-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="72554-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="72554-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="72554-123">Sféra ověření určuje nejméně název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="72554-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="72554-124">Můžete také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="72554-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="72554-125">Sféra ověření k určení, která z nich několik možných uživatelská jména a hesla je možné dotazovat uživatele.</span><span class="sxs-lookup"><span data-stu-id="72554-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="72554-126">clientCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="72554-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="72554-127">Hodnota</span><span class="sxs-lookup"><span data-stu-id="72554-127">Value</span></span>|<span data-ttu-id="72554-128">Popis</span><span class="sxs-lookup"><span data-stu-id="72554-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="72554-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="72554-129">None</span></span>|<span data-ttu-id="72554-130">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="72554-130">Security is disabled.</span></span>|  
|<span data-ttu-id="72554-131">Základní</span><span class="sxs-lookup"><span data-stu-id="72554-131">Basic</span></span>|<span data-ttu-id="72554-132">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="72554-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="72554-133">ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="72554-133">Digest</span></span>|<span data-ttu-id="72554-134">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="72554-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="72554-135">Ntlm</span><span class="sxs-lookup"><span data-stu-id="72554-135">Ntlm</span></span>|<span data-ttu-id="72554-136">Ověřování protokolem NTLM se používá jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="72554-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="72554-137">Windows</span><span class="sxs-lookup"><span data-stu-id="72554-137">Windows</span></span>|<span data-ttu-id="72554-138">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="72554-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="72554-139">Certifikát</span><span class="sxs-lookup"><span data-stu-id="72554-139">Certificate</span></span>|<span data-ttu-id="72554-140">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="72554-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="72554-141">proxyCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="72554-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="72554-142">Value</span><span class="sxs-lookup"><span data-stu-id="72554-142">Value</span></span>|<span data-ttu-id="72554-143">Popis</span><span class="sxs-lookup"><span data-stu-id="72554-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="72554-144">Žádné</span><span class="sxs-lookup"><span data-stu-id="72554-144">None</span></span>|<span data-ttu-id="72554-145">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="72554-145">Security is disabled.</span></span>|  
|<span data-ttu-id="72554-146">Základní</span><span class="sxs-lookup"><span data-stu-id="72554-146">Basic</span></span>|<span data-ttu-id="72554-147">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="72554-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="72554-148">ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="72554-148">Digest</span></span>|<span data-ttu-id="72554-149">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="72554-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="72554-150">Ntlm</span><span class="sxs-lookup"><span data-stu-id="72554-150">Ntlm</span></span>|<span data-ttu-id="72554-151">Používá NTLM jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="72554-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="72554-152">Windows</span><span class="sxs-lookup"><span data-stu-id="72554-152">Windows</span></span>|<span data-ttu-id="72554-153">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="72554-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="72554-154">Certifikát</span><span class="sxs-lookup"><span data-stu-id="72554-154">Certificate</span></span>|<span data-ttu-id="72554-155">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="72554-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72554-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="72554-156">Child Elements</span></span>  
 <span data-ttu-id="72554-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="72554-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72554-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="72554-158">Parent Elements</span></span>  
  
|<span data-ttu-id="72554-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="72554-159">Element</span></span>|<span data-ttu-id="72554-160">Popis</span><span class="sxs-lookup"><span data-stu-id="72554-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72554-161">\<security></span><span class="sxs-lookup"><span data-stu-id="72554-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="72554-162">Představuje možnosti zabezpečení [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="72554-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72554-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72554-163">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="72554-164">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="72554-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="72554-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="72554-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="72554-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="72554-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="72554-167">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="72554-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="72554-168">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="72554-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
