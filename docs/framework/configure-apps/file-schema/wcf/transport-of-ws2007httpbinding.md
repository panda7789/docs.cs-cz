---
title: '&lt;transport&gt; – &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 35af47551f742b0e48220611a874605fb752b626
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396794"
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="5bf9c-102">&lt;transport&gt; – &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5bf9c-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="5bf9c-103">Definuje nastavení ověřování pro přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="5bf9c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5bf9c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5bf9c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5bf9c-105">\<bindings></span></span>  
<span data-ttu-id="5bf9c-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="5bf9c-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="5bf9c-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5bf9c-107">\<binding></span></span>  
<span data-ttu-id="5bf9c-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="5bf9c-108">\<security></span></span>  
<span data-ttu-id="5bf9c-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="5bf9c-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf9c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bf9c-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="5bf9c-111">Typ</span><span class="sxs-lookup"><span data-stu-id="5bf9c-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bf9c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5bf9c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5bf9c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bf9c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5bf9c-114">Attributes</span></span>  
  
|<span data-ttu-id="5bf9c-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="5bf9c-115">Attribute</span></span>|<span data-ttu-id="5bf9c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5bf9c-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="5bf9c-117">Určuje přihlašovací údaje pro ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="5bf9c-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="5bf9c-119">Určuje přihlašovací údaje pro ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="5bf9c-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="5bf9c-121">Sféra ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="5bf9c-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="5bf9c-123">Sféra ověření určuje nejméně název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="5bf9c-124">Můžete také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="5bf9c-125">Sféra ověření k určení, která z nich několik možných uživatelská jména a hesla je možné dotazovat uživatele.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5bf9c-126">Typ clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="5bf9c-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5bf9c-127">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5bf9c-127">Value</span></span>|<span data-ttu-id="5bf9c-128">Popis</span><span class="sxs-lookup"><span data-stu-id="5bf9c-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5bf9c-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="5bf9c-129">None</span></span>|<span data-ttu-id="5bf9c-130">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-130">Security is disabled.</span></span>|  
|<span data-ttu-id="5bf9c-131">Základní</span><span class="sxs-lookup"><span data-stu-id="5bf9c-131">Basic</span></span>|<span data-ttu-id="5bf9c-132">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="5bf9c-133">ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="5bf9c-133">Digest</span></span>|<span data-ttu-id="5bf9c-134">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="5bf9c-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="5bf9c-135">Ntlm</span></span>|<span data-ttu-id="5bf9c-136">Ověřování protokolem NTLM se používá jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="5bf9c-137">Windows</span><span class="sxs-lookup"><span data-stu-id="5bf9c-137">Windows</span></span>|<span data-ttu-id="5bf9c-138">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="5bf9c-139">Certifikát</span><span class="sxs-lookup"><span data-stu-id="5bf9c-139">Certificate</span></span>|<span data-ttu-id="5bf9c-140">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="5bf9c-141">proxyCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="5bf9c-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5bf9c-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5bf9c-142">Value</span></span>|<span data-ttu-id="5bf9c-143">Popis</span><span class="sxs-lookup"><span data-stu-id="5bf9c-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5bf9c-144">Žádné</span><span class="sxs-lookup"><span data-stu-id="5bf9c-144">None</span></span>|<span data-ttu-id="5bf9c-145">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-145">Security is disabled.</span></span>|  
|<span data-ttu-id="5bf9c-146">Základní</span><span class="sxs-lookup"><span data-stu-id="5bf9c-146">Basic</span></span>|<span data-ttu-id="5bf9c-147">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="5bf9c-148">ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="5bf9c-148">Digest</span></span>|<span data-ttu-id="5bf9c-149">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="5bf9c-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="5bf9c-150">Ntlm</span></span>|<span data-ttu-id="5bf9c-151">Používá NTLM jako nouzové řešení pomocí domény Windows.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="5bf9c-152">Windows</span><span class="sxs-lookup"><span data-stu-id="5bf9c-152">Windows</span></span>|<span data-ttu-id="5bf9c-153">Používá integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="5bf9c-154">Certifikát</span><span class="sxs-lookup"><span data-stu-id="5bf9c-154">Certificate</span></span>|<span data-ttu-id="5bf9c-155">Certifikáty X.509 používá k ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bf9c-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5bf9c-156">Child Elements</span></span>  
 <span data-ttu-id="5bf9c-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="5bf9c-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bf9c-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5bf9c-158">Parent Elements</span></span>  
  
|<span data-ttu-id="5bf9c-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="5bf9c-159">Element</span></span>|<span data-ttu-id="5bf9c-160">Popis</span><span class="sxs-lookup"><span data-stu-id="5bf9c-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bf9c-161">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="5bf9c-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="5bf9c-162">Představuje možnosti zabezpečení [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="5bf9c-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bf9c-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bf9c-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="5bf9c-164">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5bf9c-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5bf9c-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="5bf9c-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5bf9c-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5bf9c-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5bf9c-167">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="5bf9c-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5bf9c-168">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5bf9c-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
