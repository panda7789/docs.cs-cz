---
title: "&lt;transport&gt; – &lt;ws2007HttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 573b7fb5cf130d0a638326b87ae49f90db881df4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="bac6f-102">&lt;transport&gt; – &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="bac6f-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="bac6f-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="bac6f-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="bac6f-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bac6f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bac6f-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="bac6f-105">\<bindings></span></span>  
<span data-ttu-id="bac6f-106">\<– ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="bac6f-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="bac6f-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="bac6f-107">\<binding></span></span>  
<span data-ttu-id="bac6f-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="bac6f-108">\<security></span></span>  
<span data-ttu-id="bac6f-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="bac6f-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac6f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bac6f-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="bac6f-111">Typ</span><span class="sxs-lookup"><span data-stu-id="bac6f-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bac6f-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bac6f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bac6f-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bac6f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bac6f-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="bac6f-114">Attributes</span></span>  
  
|<span data-ttu-id="bac6f-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="bac6f-115">Attribute</span></span>|<span data-ttu-id="bac6f-116">Popis</span><span class="sxs-lookup"><span data-stu-id="bac6f-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="bac6f-117">Určuje, že pověření použitá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="bac6f-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="bac6f-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="bac6f-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="bac6f-119">Určuje, že pověření použitá k ověření klienta pro proxy server domény.</span><span class="sxs-lookup"><span data-stu-id="bac6f-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="bac6f-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="bac6f-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="bac6f-121">Sféra ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="bac6f-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="bac6f-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="bac6f-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="bac6f-123">Sféra ověření určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="bac6f-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="bac6f-124">Můžete také specifikovat kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="bac6f-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="bac6f-125">Uživatele můžete dotazovat sféry ověřování k určení, který z nich několik možných uživatelská jména a hesla je možné.</span><span class="sxs-lookup"><span data-stu-id="bac6f-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="bac6f-126">clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="bac6f-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="bac6f-127">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bac6f-127">Value</span></span>|<span data-ttu-id="bac6f-128">Popis</span><span class="sxs-lookup"><span data-stu-id="bac6f-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bac6f-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="bac6f-129">None</span></span>|<span data-ttu-id="bac6f-130">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="bac6f-130">Security is disabled.</span></span>|  
|<span data-ttu-id="bac6f-131">Základní</span><span class="sxs-lookup"><span data-stu-id="bac6f-131">Basic</span></span>|<span data-ttu-id="bac6f-132">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="bac6f-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="bac6f-133">Ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="bac6f-133">Digest</span></span>|<span data-ttu-id="bac6f-134">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="bac6f-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="bac6f-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="bac6f-135">Ntlm</span></span>|<span data-ttu-id="bac6f-136">Ověřování protokolem NTLM se používá jako nouzové řešení s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bac6f-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="bac6f-137">Windows</span><span class="sxs-lookup"><span data-stu-id="bac6f-137">Windows</span></span>|<span data-ttu-id="bac6f-138">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bac6f-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="bac6f-139">certifikát</span><span class="sxs-lookup"><span data-stu-id="bac6f-139">Certificate</span></span>|<span data-ttu-id="bac6f-140">K ověření klienta používá certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="bac6f-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="bac6f-141">proxyCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="bac6f-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="bac6f-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bac6f-142">Value</span></span>|<span data-ttu-id="bac6f-143">Popis</span><span class="sxs-lookup"><span data-stu-id="bac6f-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bac6f-144">Žádné</span><span class="sxs-lookup"><span data-stu-id="bac6f-144">None</span></span>|<span data-ttu-id="bac6f-145">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="bac6f-145">Security is disabled.</span></span>|  
|<span data-ttu-id="bac6f-146">Základní</span><span class="sxs-lookup"><span data-stu-id="bac6f-146">Basic</span></span>|<span data-ttu-id="bac6f-147">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="bac6f-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="bac6f-148">Ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="bac6f-148">Digest</span></span>|<span data-ttu-id="bac6f-149">Použití ověřování algoritmem digest.</span><span class="sxs-lookup"><span data-stu-id="bac6f-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="bac6f-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="bac6f-150">Ntlm</span></span>|<span data-ttu-id="bac6f-151">Používá protokol NTLM jako nouzové řešení s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bac6f-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="bac6f-152">Windows</span><span class="sxs-lookup"><span data-stu-id="bac6f-152">Windows</span></span>|<span data-ttu-id="bac6f-153">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="bac6f-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="bac6f-154">certifikát</span><span class="sxs-lookup"><span data-stu-id="bac6f-154">Certificate</span></span>|<span data-ttu-id="bac6f-155">K ověření klienta používá certifikáty X.509.</span><span class="sxs-lookup"><span data-stu-id="bac6f-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bac6f-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bac6f-156">Child Elements</span></span>  
 <span data-ttu-id="bac6f-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="bac6f-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bac6f-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bac6f-158">Parent Elements</span></span>  
  
|<span data-ttu-id="bac6f-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="bac6f-159">Element</span></span>|<span data-ttu-id="bac6f-160">Popis</span><span class="sxs-lookup"><span data-stu-id="bac6f-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bac6f-161">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="bac6f-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="bac6f-162">Představuje možnosti zabezpečení [ \<– ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="bac6f-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bac6f-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="bac6f-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="bac6f-164">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="bac6f-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="bac6f-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="bac6f-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="bac6f-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="bac6f-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="bac6f-167">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="bac6f-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="bac6f-168">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="bac6f-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
