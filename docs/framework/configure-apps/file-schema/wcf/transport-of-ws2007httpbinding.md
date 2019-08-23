---
title: <transport> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: ce8b2acb7d87b094958e20ca0b6cca9fc8266a8d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911977"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="ae652-102">\<> přenosu > \<WS2007HttpBinding</span><span class="sxs-lookup"><span data-stu-id="ae652-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="ae652-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="ae652-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="ae652-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae652-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ae652-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="ae652-105">\<bindings></span></span>  
<span data-ttu-id="ae652-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="ae652-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="ae652-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="ae652-107">\<binding></span></span>  
<span data-ttu-id="ae652-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ae652-108">\<security></span></span>  
<span data-ttu-id="ae652-109">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="ae652-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae652-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae652-110">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="ae652-111">type</span><span class="sxs-lookup"><span data-stu-id="ae652-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae652-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ae652-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ae652-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ae652-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae652-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="ae652-114">Attributes</span></span>  
  
|<span data-ttu-id="ae652-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="ae652-115">Attribute</span></span>|<span data-ttu-id="ae652-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ae652-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="ae652-117">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="ae652-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="ae652-118">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ae652-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="ae652-119">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="ae652-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="ae652-120">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="ae652-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="ae652-121">Sféra ověření pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="ae652-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="ae652-122">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ae652-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="ae652-123">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="ae652-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="ae652-124">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="ae652-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="ae652-125">Uživatel může zadat dotaz na sféru ověření, aby mohl zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="ae652-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="ae652-126">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="ae652-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ae652-127">Value</span><span class="sxs-lookup"><span data-stu-id="ae652-127">Value</span></span>|<span data-ttu-id="ae652-128">Popis</span><span class="sxs-lookup"><span data-stu-id="ae652-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ae652-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae652-129">None</span></span>|<span data-ttu-id="ae652-130">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="ae652-130">Security is disabled.</span></span>|  
|<span data-ttu-id="ae652-131">Základní</span><span class="sxs-lookup"><span data-stu-id="ae652-131">Basic</span></span>|<span data-ttu-id="ae652-132">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="ae652-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="ae652-133">Otisk</span><span class="sxs-lookup"><span data-stu-id="ae652-133">Digest</span></span>|<span data-ttu-id="ae652-134">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="ae652-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="ae652-135">NTLM</span><span class="sxs-lookup"><span data-stu-id="ae652-135">Ntlm</span></span>|<span data-ttu-id="ae652-136">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ae652-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="ae652-137">Windows</span><span class="sxs-lookup"><span data-stu-id="ae652-137">Windows</span></span>|<span data-ttu-id="ae652-138">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ae652-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="ae652-139">Certifikát</span><span class="sxs-lookup"><span data-stu-id="ae652-139">Certificate</span></span>|<span data-ttu-id="ae652-140">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="ae652-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="ae652-141">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="ae652-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="ae652-142">Value</span><span class="sxs-lookup"><span data-stu-id="ae652-142">Value</span></span>|<span data-ttu-id="ae652-143">Popis</span><span class="sxs-lookup"><span data-stu-id="ae652-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ae652-144">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae652-144">None</span></span>|<span data-ttu-id="ae652-145">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="ae652-145">Security is disabled.</span></span>|  
|<span data-ttu-id="ae652-146">Základní</span><span class="sxs-lookup"><span data-stu-id="ae652-146">Basic</span></span>|<span data-ttu-id="ae652-147">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="ae652-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="ae652-148">Otisk</span><span class="sxs-lookup"><span data-stu-id="ae652-148">Digest</span></span>|<span data-ttu-id="ae652-149">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="ae652-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="ae652-150">NTLM</span><span class="sxs-lookup"><span data-stu-id="ae652-150">Ntlm</span></span>|<span data-ttu-id="ae652-151">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ae652-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="ae652-152">Windows</span><span class="sxs-lookup"><span data-stu-id="ae652-152">Windows</span></span>|<span data-ttu-id="ae652-153">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="ae652-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="ae652-154">Certifikát</span><span class="sxs-lookup"><span data-stu-id="ae652-154">Certificate</span></span>|<span data-ttu-id="ae652-155">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="ae652-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae652-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ae652-156">Child Elements</span></span>  
 <span data-ttu-id="ae652-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae652-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae652-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ae652-158">Parent Elements</span></span>  
  
|<span data-ttu-id="ae652-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="ae652-159">Element</span></span>|<span data-ttu-id="ae652-160">Popis</span><span class="sxs-lookup"><span data-stu-id="ae652-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae652-161">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ae652-161">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="ae652-162">Představuje možnosti [ \<zabezpečení elementu WS2007HttpBinding >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ae652-162">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae652-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae652-163">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="ae652-164">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ae652-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ae652-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="ae652-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ae652-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="ae652-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ae652-167">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ae652-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ae652-168">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="ae652-168">\<binding></span></span>](../../../misc/binding.md)
