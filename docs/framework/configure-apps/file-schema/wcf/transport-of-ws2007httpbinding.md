---
title: <transport> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 4ea60ccaba58bc0b3fa8f2263295bf1413d25e89
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399271"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="38c32-102">\<> přenosu > \<WS2007HttpBinding</span><span class="sxs-lookup"><span data-stu-id="38c32-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="38c32-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="38c32-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="38c32-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="38c32-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="38c32-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="38c32-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="38c32-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="38c32-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="38c32-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="38c32-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="38c32-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="38c32-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="38c32-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="38c32-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="38c32-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> přenosu**</span><span class="sxs-lookup"><span data-stu-id="38c32-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38c32-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38c32-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="38c32-112">type</span><span class="sxs-lookup"><span data-stu-id="38c32-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38c32-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="38c32-113">Attributes and Elements</span></span>  
 <span data-ttu-id="38c32-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="38c32-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38c32-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="38c32-115">Attributes</span></span>  
  
|<span data-ttu-id="38c32-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="38c32-116">Attribute</span></span>|<span data-ttu-id="38c32-117">Popis</span><span class="sxs-lookup"><span data-stu-id="38c32-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="38c32-118">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="38c32-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="38c32-119">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="38c32-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="38c32-120">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="38c32-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="38c32-121">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="38c32-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="38c32-122">Sféra ověření pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="38c32-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="38c32-123">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="38c32-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="38c32-124">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="38c32-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="38c32-125">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="38c32-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="38c32-126">Uživatel může zadat dotaz na sféru ověření, aby mohl zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="38c32-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="38c32-127">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="38c32-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="38c32-128">Value</span><span class="sxs-lookup"><span data-stu-id="38c32-128">Value</span></span>|<span data-ttu-id="38c32-129">Popis</span><span class="sxs-lookup"><span data-stu-id="38c32-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38c32-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="38c32-130">None</span></span>|<span data-ttu-id="38c32-131">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="38c32-131">Security is disabled.</span></span>|  
|<span data-ttu-id="38c32-132">Základní</span><span class="sxs-lookup"><span data-stu-id="38c32-132">Basic</span></span>|<span data-ttu-id="38c32-133">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="38c32-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="38c32-134">Otisk</span><span class="sxs-lookup"><span data-stu-id="38c32-134">Digest</span></span>|<span data-ttu-id="38c32-135">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="38c32-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="38c32-136">NTLM</span><span class="sxs-lookup"><span data-stu-id="38c32-136">Ntlm</span></span>|<span data-ttu-id="38c32-137">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="38c32-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="38c32-138">Windows</span><span class="sxs-lookup"><span data-stu-id="38c32-138">Windows</span></span>|<span data-ttu-id="38c32-139">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="38c32-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="38c32-140">Certifikát</span><span class="sxs-lookup"><span data-stu-id="38c32-140">Certificate</span></span>|<span data-ttu-id="38c32-141">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="38c32-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="38c32-142">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="38c32-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="38c32-143">Value</span><span class="sxs-lookup"><span data-stu-id="38c32-143">Value</span></span>|<span data-ttu-id="38c32-144">Popis</span><span class="sxs-lookup"><span data-stu-id="38c32-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38c32-145">Žádné</span><span class="sxs-lookup"><span data-stu-id="38c32-145">None</span></span>|<span data-ttu-id="38c32-146">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="38c32-146">Security is disabled.</span></span>|  
|<span data-ttu-id="38c32-147">Základní</span><span class="sxs-lookup"><span data-stu-id="38c32-147">Basic</span></span>|<span data-ttu-id="38c32-148">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="38c32-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="38c32-149">Otisk</span><span class="sxs-lookup"><span data-stu-id="38c32-149">Digest</span></span>|<span data-ttu-id="38c32-150">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="38c32-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="38c32-151">NTLM</span><span class="sxs-lookup"><span data-stu-id="38c32-151">Ntlm</span></span>|<span data-ttu-id="38c32-152">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="38c32-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="38c32-153">Windows</span><span class="sxs-lookup"><span data-stu-id="38c32-153">Windows</span></span>|<span data-ttu-id="38c32-154">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="38c32-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="38c32-155">Certifikát</span><span class="sxs-lookup"><span data-stu-id="38c32-155">Certificate</span></span>|<span data-ttu-id="38c32-156">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="38c32-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38c32-157">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="38c32-157">Child Elements</span></span>  
 <span data-ttu-id="38c32-158">Žádné</span><span class="sxs-lookup"><span data-stu-id="38c32-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38c32-159">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="38c32-159">Parent Elements</span></span>  
  
|<span data-ttu-id="38c32-160">Prvek</span><span class="sxs-lookup"><span data-stu-id="38c32-160">Element</span></span>|<span data-ttu-id="38c32-161">Popis</span><span class="sxs-lookup"><span data-stu-id="38c32-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38c32-162">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="38c32-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="38c32-163">Představuje možnosti [ \<zabezpečení elementu WS2007HttpBinding >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="38c32-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38c32-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38c32-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="38c32-165">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="38c32-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="38c32-166">Vazby</span><span class="sxs-lookup"><span data-stu-id="38c32-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="38c32-167">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="38c32-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="38c32-168">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="38c32-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="38c32-169">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="38c32-169">\<binding></span></span>](../../../misc/binding.md)
