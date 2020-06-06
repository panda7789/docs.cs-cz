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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154787"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="8f530-102">\<proxy> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8f530-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="8f530-103">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="8f530-103">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="8f530-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f530-104">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified"
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f530-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8f530-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8f530-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8f530-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f530-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8f530-107">Attributes</span></span>  
  
|<span data-ttu-id="8f530-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="8f530-108">**Attribute**</span></span>|<span data-ttu-id="8f530-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8f530-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="8f530-110">Určuje, jestli se proxy server automaticky detekuje.</span><span class="sxs-lookup"><span data-stu-id="8f530-110">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="8f530-111">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="8f530-111">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="8f530-112">Určuje, jestli se proxy server pro místní prostředky obejít.</span><span class="sxs-lookup"><span data-stu-id="8f530-112">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="8f530-113">Místní prostředky zahrnují místní server ( `http://localhost` , `http://loopback` , nebo `http://127.0.0.1` ) a identifikátor URI bez tečky ( `http://webserver` ).</span><span class="sxs-lookup"><span data-stu-id="8f530-113">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="8f530-114">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="8f530-114">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="8f530-115">Určuje identifikátor URI proxy serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="8f530-115">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="8f530-116">Určuje umístění konfiguračního skriptu.</span><span class="sxs-lookup"><span data-stu-id="8f530-116">Specifies the location of the configuration script.</span></span> <span data-ttu-id="8f530-117">Nepoužívejte `bypassonlocal` atribut s tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="8f530-117">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="8f530-118">Určuje, jestli se má používat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8f530-118">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="8f530-119">Pokud je nastaveno na `true` , budou následující atributy přepsat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="8f530-119">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="8f530-120">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="8f530-120">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f530-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8f530-121">Child Elements</span></span>  
 <span data-ttu-id="8f530-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="8f530-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f530-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8f530-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8f530-124">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="8f530-124">**Element**</span></span>|<span data-ttu-id="8f530-125">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8f530-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8f530-126">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="8f530-126">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="8f530-127">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="8f530-127">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="8f530-128">Textová hodnota</span><span class="sxs-lookup"><span data-stu-id="8f530-128">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f530-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f530-129">Remarks</span></span>  
 <span data-ttu-id="8f530-130">`proxy`Prvek definuje proxy server pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8f530-130">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="8f530-131">Pokud tento prvek v konfiguračním souboru chybí, .NET Framework použije nastavení proxy serveru v Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="8f530-131">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="8f530-132">Hodnota `proxyaddress` atributu musí být ve správném formátu (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="8f530-132">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="8f530-133">`scriptLocation`Atribut odkazuje na automatické zjišťování skriptů konfigurace proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="8f530-133">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="8f530-134"><xref:System.Net.WebProxy>Třída se pokusí najít konfigurační skript (obvykle nazvaný WPAD. dat), pokud je v aplikaci Internet Explorer vybraná možnost **použít skript automatické konfigurace** .</span><span class="sxs-lookup"><span data-stu-id="8f530-134">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="8f530-135">Pokud `bypassonlocal` je nastavená na libovolnou hodnotu, `scriptLocation` ignoruje se.</span><span class="sxs-lookup"><span data-stu-id="8f530-135">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="8f530-136">Použijte `usesystemdefault` atribut pro aplikace .NET Framework verze 1,1, které migrují na verzi 2,0.</span><span class="sxs-lookup"><span data-stu-id="8f530-136">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="8f530-137">Pokud `proxyaddress` atribut specifikuje neplatný výchozí proxy server, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8f530-137">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="8f530-138"><xref:System.Exception.InnerException%2A>Vlastnost výjimky by měla obsahovat další informace o hlavní příčině chyby.</span><span class="sxs-lookup"><span data-stu-id="8f530-138">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8f530-139">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="8f530-139">Configuration Files</span></span>  
 <span data-ttu-id="8f530-140">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8f530-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f530-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f530-141">Example</span></span>  
 <span data-ttu-id="8f530-142">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy server pro místní přístup.</span><span class="sxs-lookup"><span data-stu-id="8f530-142">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f530-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f530-143">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="8f530-144">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8f530-144">Network Settings Schema</span></span>](index.md)
