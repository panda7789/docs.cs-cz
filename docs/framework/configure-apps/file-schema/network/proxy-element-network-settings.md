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
ms.openlocfilehash: 8df9bbf2615776c2e023f03401785da95b2226eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674484"
---
# <a name="proxy-element-network-settings"></a><span data-ttu-id="13b01-102">\<proxy server > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="13b01-102">\<proxy> Element (Network Settings)</span></span>
<span data-ttu-id="13b01-103">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="13b01-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="13b01-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="13b01-104">\<configuration></span></span>  
<span data-ttu-id="13b01-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="13b01-105">\<system.net></span></span>  
<span data-ttu-id="13b01-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="13b01-106">\<defaultProxy></span></span>  
<span data-ttu-id="13b01-107">\<proxy></span><span class="sxs-lookup"><span data-stu-id="13b01-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13b01-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13b01-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13b01-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="13b01-109">Attributes and Elements</span></span>  
 <span data-ttu-id="13b01-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="13b01-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13b01-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="13b01-111">Attributes</span></span>  
  
|<span data-ttu-id="13b01-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="13b01-112">**Attribute**</span></span>|<span data-ttu-id="13b01-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="13b01-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="13b01-114">Určuje, zda je automaticky zjišťován proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="13b01-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="13b01-115">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="13b01-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="13b01-116">Určuje, zda je pro místní prostředky obejít proxy server.</span><span class="sxs-lookup"><span data-stu-id="13b01-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="13b01-117">Místní prostředky zahrnují místní server (`http://localhost`, `http://loopback`, nebo `http://127.0.0.1`) a identifikátor URI bez období (`http://webserver`).</span><span class="sxs-lookup"><span data-stu-id="13b01-117">Local resources include the local server (`http://localhost`, `http://loopback`, or `http://127.0.0.1`) and a URI without a period (`http://webserver`).</span></span> <span data-ttu-id="13b01-118">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="13b01-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="13b01-119">Určuje identifikátor URI pro použití proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="13b01-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="13b01-120">Určuje umístění skriptu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="13b01-120">Specifies the location of the configuration script.</span></span> <span data-ttu-id="13b01-121">Nepoužívejte `bypassonlocal` atribut k tomuto atributu.</span><span class="sxs-lookup"><span data-stu-id="13b01-121">Do not use the `bypassonlocal` attribute with this attribute.</span></span> |  
|`usesystemdefault`|<span data-ttu-id="13b01-122">Určuje, jestli se má používat nastavení proxy aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="13b01-122">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="13b01-123">Pokud nastavit `true`, následující atributy se přepíše nastavení proxy aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="13b01-123">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="13b01-124">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="13b01-124">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13b01-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="13b01-125">Child Elements</span></span>  
 <span data-ttu-id="13b01-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="13b01-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13b01-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="13b01-127">Parent Elements</span></span>  
  
|<span data-ttu-id="13b01-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="13b01-128">**Element**</span></span>|<span data-ttu-id="13b01-129">**Popis**</span><span class="sxs-lookup"><span data-stu-id="13b01-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="13b01-130">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="13b01-130">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="13b01-131">Konfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="13b01-131">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="13b01-132">Textová hodnota</span><span class="sxs-lookup"><span data-stu-id="13b01-132">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13b01-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13b01-133">Remarks</span></span>  
 <span data-ttu-id="13b01-134">`proxy` Element definuje proxy server pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="13b01-134">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="13b01-135">Pokud tento prvek v konfiguračním souboru chybí, použije rozhraní .NET Framework v aplikaci Internet Explorer nastavení proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="13b01-135">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="13b01-136">Hodnota `proxyaddress` atribut by měl mít ve správném formátu indikátor URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="13b01-136">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="13b01-137">`scriptLocation` Atribut odkazuje na automatické zjišťování proxy konfigurační skripty.</span><span class="sxs-lookup"><span data-stu-id="13b01-137">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="13b01-138"><xref:System.Net.WebProxy> Třídy se pokusí najít konfigurační skript (obvykle s názvem Wpad.dat) Pokud **použít automatický konfigurační skript** je vybraná možnost v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="13b01-138">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span> <span data-ttu-id="13b01-139">Pokud `bypassonlocal` je nastavena na libovolnou hodnotu `scriptLocation` se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="13b01-139">If `bypassonlocal` is set to any value, `scriptLocation` is ignored.</span></span>
  
 <span data-ttu-id="13b01-140">Použití `usesystemdefault` atribut pro aplikace .NET Framework verze 1.1, které migrují na verzi 2.0.</span><span class="sxs-lookup"><span data-stu-id="13b01-140">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="13b01-141">Pokud je vyvolána výjimka `proxyaddress` atribut specifikuje neplatný výchozí proxy.</span><span class="sxs-lookup"><span data-stu-id="13b01-141">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="13b01-142"><xref:System.Exception.InnerException%2A> Vlastnosti výjimky by měl mít další informace o hlavní příčinu chyby.</span><span class="sxs-lookup"><span data-stu-id="13b01-142">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="13b01-143">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="13b01-143">Configuration Files</span></span>  
 <span data-ttu-id="13b01-144">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="13b01-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13b01-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="13b01-145">Example</span></span>  
 <span data-ttu-id="13b01-146">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy pro místní přístup.</span><span class="sxs-lookup"><span data-stu-id="13b01-146">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13b01-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13b01-147">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="13b01-148">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="13b01-148">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
