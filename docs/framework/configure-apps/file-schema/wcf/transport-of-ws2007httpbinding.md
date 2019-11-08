---
title: <transport> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732759"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="0ff53-102">> \<přenosů \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0ff53-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="0ff53-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="0ff53-103">Defines authentication settings for the HTTP transport.</span></span>  
  
<span data-ttu-id="0ff53-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0ff53-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0ff53-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="0ff53-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0ff53-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0ff53-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0ff53-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="0ff53-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="0ff53-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="0ff53-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="0ff53-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="0ff53-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)</span></span>\
<span data-ttu-id="0ff53-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**</span><span class="sxs-lookup"><span data-stu-id="0ff53-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ff53-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ff53-111">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="0ff53-112">Typ</span><span class="sxs-lookup"><span data-stu-id="0ff53-112">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ff53-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0ff53-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0ff53-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0ff53-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ff53-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="0ff53-115">Attributes</span></span>  
  
|<span data-ttu-id="0ff53-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="0ff53-116">Attribute</span></span>|<span data-ttu-id="0ff53-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0ff53-117">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="0ff53-118">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="0ff53-118">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="0ff53-119">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="0ff53-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="0ff53-120">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="0ff53-120">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="0ff53-121">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="0ff53-121">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="0ff53-122">Sféra ověření pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="0ff53-122">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="0ff53-123">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="0ff53-123">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="0ff53-124">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="0ff53-124">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="0ff53-125">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="0ff53-125">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="0ff53-126">Uživatel může zadat dotaz na sféru ověření, aby mohl zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="0ff53-126">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="0ff53-127">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="0ff53-127">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="0ff53-128">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0ff53-128">Value</span></span>|<span data-ttu-id="0ff53-129">Popis</span><span class="sxs-lookup"><span data-stu-id="0ff53-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0ff53-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ff53-130">None</span></span>|<span data-ttu-id="0ff53-131">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="0ff53-131">Security is disabled.</span></span>|  
|<span data-ttu-id="0ff53-132">Základní</span><span class="sxs-lookup"><span data-stu-id="0ff53-132">Basic</span></span>|<span data-ttu-id="0ff53-133">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="0ff53-133">Uses basic authentication.</span></span>|  
|<span data-ttu-id="0ff53-134">otisk</span><span class="sxs-lookup"><span data-stu-id="0ff53-134">Digest</span></span>|<span data-ttu-id="0ff53-135">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="0ff53-135">Uses digest authentication.</span></span>|  
|<span data-ttu-id="0ff53-136">NTLM</span><span class="sxs-lookup"><span data-stu-id="0ff53-136">Ntlm</span></span>|<span data-ttu-id="0ff53-137">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0ff53-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="0ff53-138">Windows</span><span class="sxs-lookup"><span data-stu-id="0ff53-138">Windows</span></span>|<span data-ttu-id="0ff53-139">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0ff53-139">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="0ff53-140">Certifikát</span><span class="sxs-lookup"><span data-stu-id="0ff53-140">Certificate</span></span>|<span data-ttu-id="0ff53-141">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="0ff53-141">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="0ff53-142">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="0ff53-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="0ff53-143">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0ff53-143">Value</span></span>|<span data-ttu-id="0ff53-144">Popis</span><span class="sxs-lookup"><span data-stu-id="0ff53-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0ff53-145">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ff53-145">None</span></span>|<span data-ttu-id="0ff53-146">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="0ff53-146">Security is disabled.</span></span>|  
|<span data-ttu-id="0ff53-147">Základní</span><span class="sxs-lookup"><span data-stu-id="0ff53-147">Basic</span></span>|<span data-ttu-id="0ff53-148">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="0ff53-148">Uses basic authentication.</span></span>|  
|<span data-ttu-id="0ff53-149">otisk</span><span class="sxs-lookup"><span data-stu-id="0ff53-149">Digest</span></span>|<span data-ttu-id="0ff53-150">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="0ff53-150">Uses digest authentication.</span></span>|  
|<span data-ttu-id="0ff53-151">NTLM</span><span class="sxs-lookup"><span data-stu-id="0ff53-151">Ntlm</span></span>|<span data-ttu-id="0ff53-152">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0ff53-152">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="0ff53-153">Windows</span><span class="sxs-lookup"><span data-stu-id="0ff53-153">Windows</span></span>|<span data-ttu-id="0ff53-154">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0ff53-154">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="0ff53-155">Certifikát</span><span class="sxs-lookup"><span data-stu-id="0ff53-155">Certificate</span></span>|<span data-ttu-id="0ff53-156">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="0ff53-156">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ff53-157">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0ff53-157">Child Elements</span></span>  
 <span data-ttu-id="0ff53-158">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ff53-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ff53-159">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0ff53-159">Parent Elements</span></span>  
  
|<span data-ttu-id="0ff53-160">Prvek</span><span class="sxs-lookup"><span data-stu-id="0ff53-160">Element</span></span>|<span data-ttu-id="0ff53-161">Popis</span><span class="sxs-lookup"><span data-stu-id="0ff53-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0ff53-162">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="0ff53-162">\<security></span></span>](security-of-ws2007httpbinding.md)|<span data-ttu-id="0ff53-163">Představuje možnosti zabezpečení [\<ws2007HttpBinding >](ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="0ff53-163">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ff53-164">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ff53-164">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="0ff53-165">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0ff53-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0ff53-166">Vazby</span><span class="sxs-lookup"><span data-stu-id="0ff53-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0ff53-167">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="0ff53-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0ff53-168">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="0ff53-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0ff53-169">vazba \<</span><span class="sxs-lookup"><span data-stu-id="0ff53-169">\<binding></span></span>](bindings.md)
