---
title: <proxy> – element (nastavení sítě)
description: <proxy>Prvek nastavení sítě definuje možnosti proxy server v .NET Framework. Tento článek obsahuje příklad.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
ms.openlocfilehash: 8ae30b8c29dcf3aaa183ff295c7ee8592322797f
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141778"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="54ae6-104">\<proxy> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="54ae6-104">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="54ae6-105">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="54ae6-105">Defines a proxy server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<proxy>**

## <a name="syntax"></a><span data-ttu-id="54ae6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="54ae6-106">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="True|False|Unspecified"
  bypassonlocal="True|False|Unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="True|False|Unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54ae6-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="54ae6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="54ae6-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="54ae6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54ae6-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="54ae6-109">Attributes</span></span>  
  
|<span data-ttu-id="54ae6-110">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="54ae6-110">**Attribute**</span></span>|<span data-ttu-id="54ae6-111">**Popis**</span><span class="sxs-lookup"><span data-stu-id="54ae6-111">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="54ae6-112">Určuje, jestli se proxy server automaticky detekuje.</span><span class="sxs-lookup"><span data-stu-id="54ae6-112">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="54ae6-113">Výchozí hodnota je `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="54ae6-113">The default value is `Unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="54ae6-114">Určuje, jestli se proxy server pro místní prostředky obejít.</span><span class="sxs-lookup"><span data-stu-id="54ae6-114">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="54ae6-115">Místní prostředky zahrnují místní server ( `http://localhost` , `http://loopback` , nebo `http://127.0.0.1` ) a identifikátor URI bez tečky ( `http://webserver` ).</span><span class="sxs-lookup"><span data-stu-id="54ae6-115">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="54ae6-116">Výchozí hodnota je `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="54ae6-116">The default value is `Unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="54ae6-117">Určuje identifikátor URI proxy serveru, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="54ae6-117">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="54ae6-118">Určuje umístění konfiguračního skriptu.</span><span class="sxs-lookup"><span data-stu-id="54ae6-118">Specifies the location of the configuration script.</span></span> <span data-ttu-id="54ae6-119">Nepoužívejte `bypassonlocal` atribut s tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="54ae6-119">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="54ae6-120">Určuje, jestli se má používat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="54ae6-120">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="54ae6-121">Pokud je nastaveno na `True` , budou následující atributy přepsat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="54ae6-121">If set to `True`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="54ae6-122">Výchozí hodnota je `Unspecified`.</span><span class="sxs-lookup"><span data-stu-id="54ae6-122">The default value is `Unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54ae6-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="54ae6-123">Child Elements</span></span>  
 <span data-ttu-id="54ae6-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="54ae6-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54ae6-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="54ae6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="54ae6-126">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="54ae6-126">**Element**</span></span>|<span data-ttu-id="54ae6-127">**Popis**</span><span class="sxs-lookup"><span data-stu-id="54ae6-127">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="54ae6-128">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="54ae6-128">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="54ae6-129">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="54ae6-129">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="54ae6-130">Textová hodnota</span><span class="sxs-lookup"><span data-stu-id="54ae6-130">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54ae6-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54ae6-131">Remarks</span></span>  
 <span data-ttu-id="54ae6-132">`proxy`Prvek definuje proxy server pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="54ae6-132">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="54ae6-133">Pokud tento prvek v konfiguračním souboru chybí, .NET Framework použije nastavení proxy serveru v Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="54ae6-133">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="54ae6-134">Hodnota `proxyaddress` atributu musí být ve správném formátu (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="54ae6-134">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="54ae6-135">`scriptLocation`Atribut odkazuje na automatické zjišťování skriptů konfigurace proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="54ae6-135">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="54ae6-136"><xref:System.Net.WebProxy>Třída se pokusí najít konfigurační skript (obvykle nazvaný WPAD. dat), pokud je v aplikaci Internet Explorer vybraná možnost **použít skript automatické konfigurace** .</span><span class="sxs-lookup"><span data-stu-id="54ae6-136">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="54ae6-137">Pokud `bypassonlocal` je nastavená na libovolnou hodnotu, `scriptLocation` ignoruje se.</span><span class="sxs-lookup"><span data-stu-id="54ae6-137">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="54ae6-138">Použijte `usesystemdefault` atribut pro aplikace .NET Framework verze 1,1, které migrují na verzi 2,0.</span><span class="sxs-lookup"><span data-stu-id="54ae6-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="54ae6-139">Pokud `proxyaddress` atribut specifikuje neplatný výchozí proxy server, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="54ae6-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="54ae6-140"><xref:System.Exception.InnerException%2A>Vlastnost výjimky by měla obsahovat další informace o hlavní příčině chyby.</span><span class="sxs-lookup"><span data-stu-id="54ae6-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="54ae6-141">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="54ae6-141">Configuration Files</span></span>  
 <span data-ttu-id="54ae6-142">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="54ae6-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54ae6-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="54ae6-143">Example</span></span>  
 <span data-ttu-id="54ae6-144">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy server pro místní přístup.</span><span class="sxs-lookup"><span data-stu-id="54ae6-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="True"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="True"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54ae6-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="54ae6-145">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="54ae6-146">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="54ae6-146">Network Settings Schema</span></span>](index.md)
