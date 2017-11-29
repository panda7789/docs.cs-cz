---
title: "&lt;proxy&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/proxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#proxy
helpviewer_keywords:
- <proxy> element
- proxy element
ms.assetid: 37a548d8-fade-4ac5-82ec-b49b6c6cb22a
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7178527f369c698b0ab53aa41cb28dd0126436b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltproxygt-element-network-settings"></a><span data-ttu-id="6ec06-102">&lt;proxy&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="6ec06-102">&lt;proxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="6ec06-103">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="6ec06-103">Defines a proxy server.</span></span>  
  
 <span data-ttu-id="6ec06-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="6ec06-104">\<configuration></span></span>  
<span data-ttu-id="6ec06-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="6ec06-105">\<system.net></span></span>  
<span data-ttu-id="6ec06-106">\<defaultProxy – ></span><span class="sxs-lookup"><span data-stu-id="6ec06-106">\<defaultProxy></span></span>  
<span data-ttu-id="6ec06-107">\<proxy ></span><span class="sxs-lookup"><span data-stu-id="6ec06-107">\<proxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ec06-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ec06-108">Syntax</span></span>  
  
```xml  
<proxy
  autoDetect="true|false|unspecified" 
  bypassonlocal="true|false|unspecified"
  proxyaddress="uriString"
  scriptLocation="uriString"
  usesystemdefault="true|false|unspecified"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ec06-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6ec06-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6ec06-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6ec06-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ec06-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6ec06-111">Attributes</span></span>  
  
|<span data-ttu-id="6ec06-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="6ec06-112">**Attribute**</span></span>|<span data-ttu-id="6ec06-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="6ec06-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`autoDetect`|<span data-ttu-id="6ec06-114">Určuje, zda je automaticky zjišťován proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="6ec06-114">Specifies whether the proxy is automatically detected.</span></span> <span data-ttu-id="6ec06-115">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="6ec06-115">The default value is `unspecified`.</span></span>|  
|`bypassonlocal`|<span data-ttu-id="6ec06-116">Určuje, zda je u místních prostředků název proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="6ec06-116">Specifies whether the proxy is bypassed for local resources.</span></span> <span data-ttu-id="6ec06-117">Místní prostředky zahrnují URI bez tečky (http://webserver) a na místním serveru (http://localhost, http://loopback nebo http://127.0.0.1).</span><span class="sxs-lookup"><span data-stu-id="6ec06-117">Local resources include the local server (http://localhost, http://loopback, or http://127.0.0.1) and a URI without a period (http://webserver).</span></span> <span data-ttu-id="6ec06-118">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="6ec06-118">The default value is `unspecified`.</span></span>|  
|`proxyaddress`|<span data-ttu-id="6ec06-119">Určuje identifikátor URI k použití proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="6ec06-119">Specifies the proxy URI to use.</span></span>|  
|`scriptLocation`|<span data-ttu-id="6ec06-120">Určuje umístění konfigurační skript.</span><span class="sxs-lookup"><span data-stu-id="6ec06-120">Specifies the location of the configuration script.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="6ec06-121">Určuje, jestli se má používat nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="6ec06-121">Specifies whether to use Internet Explorer proxy settings.</span></span> <span data-ttu-id="6ec06-122">Pokud nastavena na `true`, následující atributy se přepíše nastavení proxy serveru aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="6ec06-122">If set to `true`, subsequent attributes will override Internet Explorer proxy settings.</span></span> <span data-ttu-id="6ec06-123">Výchozí hodnota je `unspecified`.</span><span class="sxs-lookup"><span data-stu-id="6ec06-123">The default value is `unspecified`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ec06-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6ec06-124">Child Elements</span></span>  
 <span data-ttu-id="6ec06-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="6ec06-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ec06-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6ec06-126">Parent Elements</span></span>  
  
|<span data-ttu-id="6ec06-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="6ec06-127">**Element**</span></span>|<span data-ttu-id="6ec06-128">**Popis**</span><span class="sxs-lookup"><span data-stu-id="6ec06-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6ec06-129">defaultProxy –</span><span class="sxs-lookup"><span data-stu-id="6ec06-129">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="6ec06-130">Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="6ec06-130">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="text-value"></a><span data-ttu-id="6ec06-131">Textová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ec06-131">Text Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ec06-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ec06-132">Remarks</span></span>  
 <span data-ttu-id="6ec06-133">`proxy` Element definuje proxy server pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6ec06-133">The `proxy` element defines a proxy server for an application.</span></span> <span data-ttu-id="6ec06-134">Pokud tento element chybí z konfiguračního souboru, potom rozhraní .NET Framework bude používat nastavení proxy serveru v Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="6ec06-134">If this element is missing from the configuration file, then the .NET Framework will use the proxy settings in Internet Explorer.</span></span>  
  
 <span data-ttu-id="6ec06-135">Hodnota `proxyaddress` atribut by měl mít ve správném formátu indikátor URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="6ec06-135">The value for the `proxyaddress` attribute should be a well-formed Uniform Resource Indicator (URI).</span></span>  
  
 <span data-ttu-id="6ec06-136">`scriptLocation` Atribut odkazuje na automatické zjišťování proxy konfigurační skripty.</span><span class="sxs-lookup"><span data-stu-id="6ec06-136">The `scriptLocation` attribute refers to the automatic detection of proxy configuration scripts.</span></span> <span data-ttu-id="6ec06-137"><xref:System.Net.WebProxy> Třídy se pokusí najít konfigurační skript (obvykle s názvem Wpad.dat) Pokud **použít automatický konfigurační skript** v aplikaci Internet Explorer je vybraná možnost.</span><span class="sxs-lookup"><span data-stu-id="6ec06-137">The <xref:System.Net.WebProxy> class will attempt to locate a configuration script (usually named Wpad.dat) when the **Use automatic configuration script** option is selected in Internet Explorer.</span></span>  
  
 <span data-ttu-id="6ec06-138">Použití `usesystemdefault` atribut pro rozhraní .NET Framework verze 1.1 aplikace, které provádíte migraci do verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="6ec06-138">Use the `usesystemdefault` attribute for .NET Framework version 1.1 applications that are migrating to version 2.0.</span></span>  
  
 <span data-ttu-id="6ec06-139">Pokud je vyvolána výjimka `proxyaddress` atribut určuje neplatná výchozí proxy server.</span><span class="sxs-lookup"><span data-stu-id="6ec06-139">An exception is thrown if the `proxyaddress` attribute specifies an invalid default proxy.</span></span> <span data-ttu-id="6ec06-140"><xref:System.Exception.InnerException%2A> Vlastnost výjimky by měl mít další informace o hlavních příčin této chyby.</span><span class="sxs-lookup"><span data-stu-id="6ec06-140">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6ec06-141">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="6ec06-141">Configuration Files</span></span>  
 <span data-ttu-id="6ec06-142">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6ec06-142">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ec06-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ec06-143">Example</span></span>  
 <span data-ttu-id="6ec06-144">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy pro místní přístup.</span><span class="sxs-lookup"><span data-stu-id="6ec06-144">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ec06-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ec06-145">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="6ec06-146">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="6ec06-146">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
