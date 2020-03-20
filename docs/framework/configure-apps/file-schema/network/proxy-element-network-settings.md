---
title: <proxy> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 590ea747c2fa9e5e85e5e9d05f6fb80fe60251d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154787"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="5be70-102">\<prvek> proxy (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="5be70-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="5be70-103">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="5be70-103">Defines a proxy server.</span></span>  

<span data-ttu-id="5be70-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5be70-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5be70-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5be70-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="5be70-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="5be70-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="5be70-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span><span class="sxs-lookup"><span data-stu-id="5be70-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5be70-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5be70-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5be70-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5be70-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5be70-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5be70-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5be70-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="5be70-111">Attributes</span></span>  
  
|<span data-ttu-id="5be70-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="5be70-112">**Attribute**</span></span>|<span data-ttu-id="5be70-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="5be70-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="5be70-114">Určuje, zda bude server proxy automaticky rozpoznán.</span><span class="sxs-lookup"><span data-stu-id="5be70-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="5be70-115">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="5be70-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="5be70-116">Určuje, zda je proxy server vynechán pro místní prostředky.</span><span class="sxs-lookup"><span data-stu-id="5be70-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="5be70-117">Mezi místní prostředky patří`http://localhost` `http://loopback`místní `http://127.0.0.1`server ( , ,`http://webserver`nebo ) a identifikátor URI bez tečky ( ).</span><span class="sxs-lookup"><span data-stu-id="5be70-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="5be70-118">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="5be70-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="5be70-119">Určuje identifikátor URI proxy serveru, který má být používán.</span><span class="sxs-lookup"><span data-stu-id="5be70-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="5be70-120">Určuje umístění konfiguračního skriptu.</span><span class="sxs-lookup"><span data-stu-id="5be70-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="5be70-121">Nepoužívejte `bypassonlocal` atribut s tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="5be70-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="5be70-122">Určuje, zda se má použít nastavení serveru proxy aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5be70-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="5be70-123">Pokud je `true`nastavena možnost , následné atributy přepíší nastavení serveru proxy aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5be70-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="5be70-124">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="5be70-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5be70-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5be70-125">Child Elements</span></span>  
 <span data-ttu-id="5be70-126">Žádné.</span><span class="sxs-lookup"><span data-stu-id="5be70-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5be70-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5be70-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5be70-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="5be70-128">**Element**</span></span>|<span data-ttu-id="5be70-129">**Popis**</span><span class="sxs-lookup"><span data-stu-id="5be70-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5be70-130">výchozí proxy</span><span class="sxs-lookup"><span data-stu-id="5be70-130">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="5be70-131">Konfiguruje proxy server HTTP (HTTP).</span><span class="sxs-lookup"><span data-stu-id="5be70-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="5be70-132">Textová hodnota</span><span class="sxs-lookup"><span data-stu-id="5be70-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5be70-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5be70-133">Remarks</span></span>  
 <span data-ttu-id="5be70-134">Prvek `proxy` definuje proxy server pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5be70-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="5be70-135">Pokud tento prvek v konfiguračním souboru chybí, použije rozhraní .NET Framework nastavení serveru proxy v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5be70-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="5be70-136">Hodnota atributu `proxyaddress` by měla být dobře tvarovaný indikátor jednotného prostředku (URI).</span><span class="sxs-lookup"><span data-stu-id="5be70-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="5be70-137">Atribut `scriptLocation` odkazuje na automatickou detekci skriptů konfigurace proxy.</span><span class="sxs-lookup"><span data-stu-id="5be70-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="5be70-138">Třída <xref:System.Net.WebProxy> se pokusí najít konfigurační skript (obvykle s názvem Wpad.dat), pokud je v aplikaci Internet Explorer vybrána možnost **Použít automatický konfigurační skript.**</span><span class="sxs-lookup"><span data-stu-id="5be70-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="5be70-139">Pokud `bypassonlocal` je nastavena `scriptLocation` na libovolnou hodnotu, je ignorována.</span><span class="sxs-lookup"><span data-stu-id="5be70-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="5be70-140">Použijte `usesystemdefault` atribut pro aplikace rozhraní .NET Framework verze 1.1, které migrují na verzi 2.0.</span><span class="sxs-lookup"><span data-stu-id="5be70-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="5be70-141">Výjimka je vyvolána, `proxyaddress` pokud atribut určuje neplatný výchozí proxy server.</span><span class="sxs-lookup"><span data-stu-id="5be70-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="5be70-142">Vlastnost <xref:System.Exception.InnerException%2A> na výjimce by měl mít další informace o hlavní příčinu chyby.</span><span class="sxs-lookup"><span data-stu-id="5be70-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5be70-143">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="5be70-143">Configuration Files</span></span>  
 <span data-ttu-id="5be70-144">Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5be70-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5be70-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="5be70-145">Example</span></span>  
 <span data-ttu-id="5be70-146">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu serveru proxy a obchází proxy server pro místní přístup.</span><span class="sxs-lookup"><span data-stu-id="5be70-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5be70-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="5be70-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="5be70-148">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="5be70-148">Network Settings Schema</span></span>](index.md)
