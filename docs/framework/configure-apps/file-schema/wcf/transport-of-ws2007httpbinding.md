---
title: <transport> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 0cd20c607b0c4ddd3ecfd806d38ba63b4a5c5a25
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732759"
---
# <a name="transport-of-ws2007httpbinding"></a><span data-ttu-id="95a47-102">\<transport> z \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="95a47-102">\<transport> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="95a47-103">Definuje nastavení ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="95a47-103">Defines authentication settings for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="95a47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95a47-104">Syntax</span></span>  
  
```xml  
<transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
           proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
           realm="string" />
```  
  
## <a name="type"></a><span data-ttu-id="95a47-105">Typ</span><span class="sxs-lookup"><span data-stu-id="95a47-105">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95a47-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="95a47-106">Attributes and Elements</span></span>  
 <span data-ttu-id="95a47-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="95a47-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95a47-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="95a47-108">Attributes</span></span>  
  
|<span data-ttu-id="95a47-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="95a47-109">Attribute</span></span>|<span data-ttu-id="95a47-110">Popis</span><span class="sxs-lookup"><span data-stu-id="95a47-110">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="95a47-111">Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="95a47-111">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="95a47-112">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="95a47-112">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="95a47-113">Určuje přihlašovací údaje, které se používají k ověření klienta na proxy doméně.</span><span class="sxs-lookup"><span data-stu-id="95a47-113">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="95a47-114">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="95a47-114">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="95a47-115">Sféra ověření pro ověřování algoritmem Digest nebo základního ověřování.</span><span class="sxs-lookup"><span data-stu-id="95a47-115">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="95a47-116">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="95a47-116">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="95a47-117">Sféra ověřování určuje alespoň název hostitele, který provádí ověřování.</span><span class="sxs-lookup"><span data-stu-id="95a47-117">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="95a47-118">Může také určit kolekci uživatelů, kteří mají přístup.</span><span class="sxs-lookup"><span data-stu-id="95a47-118">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="95a47-119">Uživatel může zadat dotaz na sféru ověření, aby mohl zjistit, který z několika možných uživatelských jmen a hesel lze použít.</span><span class="sxs-lookup"><span data-stu-id="95a47-119">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="95a47-120">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="95a47-120">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="95a47-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="95a47-121">Value</span></span>|<span data-ttu-id="95a47-122">Description</span><span class="sxs-lookup"><span data-stu-id="95a47-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="95a47-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="95a47-123">None</span></span>|<span data-ttu-id="95a47-124">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="95a47-124">Security is disabled.</span></span>|  
|<span data-ttu-id="95a47-125">Základní</span><span class="sxs-lookup"><span data-stu-id="95a47-125">Basic</span></span>|<span data-ttu-id="95a47-126">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="95a47-126">Uses basic authentication.</span></span>|  
|<span data-ttu-id="95a47-127">Otisk</span><span class="sxs-lookup"><span data-stu-id="95a47-127">Digest</span></span>|<span data-ttu-id="95a47-128">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="95a47-128">Uses digest authentication.</span></span>|  
|<span data-ttu-id="95a47-129">NTLM</span><span class="sxs-lookup"><span data-stu-id="95a47-129">Ntlm</span></span>|<span data-ttu-id="95a47-130">Používá ověřování NTLM jako zálohu v doméně systému Windows.</span><span class="sxs-lookup"><span data-stu-id="95a47-130">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="95a47-131">Windows</span><span class="sxs-lookup"><span data-stu-id="95a47-131">Windows</span></span>|<span data-ttu-id="95a47-132">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="95a47-132">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="95a47-133">Certifikát</span><span class="sxs-lookup"><span data-stu-id="95a47-133">Certificate</span></span>|<span data-ttu-id="95a47-134">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="95a47-134">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="95a47-135">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="95a47-135">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="95a47-136">Hodnota</span><span class="sxs-lookup"><span data-stu-id="95a47-136">Value</span></span>|<span data-ttu-id="95a47-137">Description</span><span class="sxs-lookup"><span data-stu-id="95a47-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="95a47-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="95a47-138">None</span></span>|<span data-ttu-id="95a47-139">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="95a47-139">Security is disabled.</span></span>|  
|<span data-ttu-id="95a47-140">Základní</span><span class="sxs-lookup"><span data-stu-id="95a47-140">Basic</span></span>|<span data-ttu-id="95a47-141">Používá základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="95a47-141">Uses basic authentication.</span></span>|  
|<span data-ttu-id="95a47-142">Otisk</span><span class="sxs-lookup"><span data-stu-id="95a47-142">Digest</span></span>|<span data-ttu-id="95a47-143">Používá ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="95a47-143">Uses digest authentication.</span></span>|  
|<span data-ttu-id="95a47-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="95a47-144">Ntlm</span></span>|<span data-ttu-id="95a47-145">Používá protokol NTLM jako zálohu s doménou systému Windows.</span><span class="sxs-lookup"><span data-stu-id="95a47-145">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="95a47-146">Windows</span><span class="sxs-lookup"><span data-stu-id="95a47-146">Windows</span></span>|<span data-ttu-id="95a47-147">Používá integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="95a47-147">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="95a47-148">Certifikát</span><span class="sxs-lookup"><span data-stu-id="95a47-148">Certificate</span></span>|<span data-ttu-id="95a47-149">Pomocí certifikátů X. 509 ověří klienta.</span><span class="sxs-lookup"><span data-stu-id="95a47-149">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95a47-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="95a47-150">Child Elements</span></span>  
 <span data-ttu-id="95a47-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="95a47-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95a47-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="95a47-152">Parent Elements</span></span>  
  
|<span data-ttu-id="95a47-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="95a47-153">Element</span></span>|<span data-ttu-id="95a47-154">Description</span><span class="sxs-lookup"><span data-stu-id="95a47-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-ws2007httpbinding.md)|<span data-ttu-id="95a47-155">Představuje možnosti zabezpečení [\<ws2007HttpBinding>](ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="95a47-155">Represents the security capabilities of the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95a47-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="95a47-156">See also</span></span>

- <xref:System.ServiceModel.HttpTransportSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>
- [<span data-ttu-id="95a47-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="95a47-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="95a47-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="95a47-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="95a47-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="95a47-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="95a47-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="95a47-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
