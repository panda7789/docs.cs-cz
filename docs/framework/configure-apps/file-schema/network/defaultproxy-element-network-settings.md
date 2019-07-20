---
title: <defaultProxy> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 5947808cd137fc4cd280ac683a3e9a14b0d4644d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363873"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="0d9cd-102">\<defaultProxy – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="0d9cd-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="0d9cd-103">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="0d9cd-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="0d9cd-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0d9cd-104">\<configuration></span></span>  
<span data-ttu-id="0d9cd-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0d9cd-105">\<system.net></span></span>  
<span data-ttu-id="0d9cd-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="0d9cd-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d9cd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d9cd-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d9cd-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0d9cd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0d9cd-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d9cd-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0d9cd-110">Attributes</span></span>  
  
|<span data-ttu-id="0d9cd-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="0d9cd-111">**Element**</span></span>|<span data-ttu-id="0d9cd-112">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0d9cd-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="0d9cd-113">Určuje, zda je použit webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="0d9cd-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="0d9cd-115">Určuje, jestli se pro přístup k webovému proxy serveru používají výchozí přihlašovací údaje pro tohoto hostitele.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="0d9cd-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d9cd-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0d9cd-117">Child Elements</span></span>  
  
|<span data-ttu-id="0d9cd-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="0d9cd-118">**Element**</span></span>|<span data-ttu-id="0d9cd-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0d9cd-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0d9cd-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="0d9cd-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="0d9cd-121">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="0d9cd-122">module</span><span class="sxs-lookup"><span data-stu-id="0d9cd-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="0d9cd-123">Přidá do aplikace nový modul proxy.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="0d9cd-124">proxy</span><span class="sxs-lookup"><span data-stu-id="0d9cd-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="0d9cd-125">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d9cd-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0d9cd-126">Parent Elements</span></span>  
  
|<span data-ttu-id="0d9cd-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="0d9cd-127">**Element**</span></span>|<span data-ttu-id="0d9cd-128">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0d9cd-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0d9cd-129">system.net</span><span class="sxs-lookup"><span data-stu-id="0d9cd-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="0d9cd-130">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d9cd-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d9cd-131">Remarks</span></span>  
 <span data-ttu-id="0d9cd-132">Pokud je Element defaultProxy prázdný, použije se nastavení proxy z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="0d9cd-133">Toto chování se liší od verze 1,1 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="0d9cd-134">Výjimka je vyvolána, pokud prvek [modulu](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) určuje typ, který není veřejný, typ není odvozen od <xref:System.Net.IWebProxy> třídy, došlo k výjimce z konstruktoru bez parametrů tohoto objektu, nebo došlo k výjimce při načítání výchozí proxy server zadaný systémem.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="0d9cd-135"><xref:System.Exception.InnerException%2A> Vlastnost výjimky by měla obsahovat další informace o hlavní příčině chyby.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0d9cd-136">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="0d9cd-136">Configuration Files</span></span>  
 <span data-ttu-id="0d9cd-137">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="0d9cd-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d9cd-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d9cd-138">Example</span></span>  
 <span data-ttu-id="0d9cd-139">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy server pro místní přístup a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="0d9cd-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        proxyaddress="http://192.168.1.10:3128"  
        bypassonlocal="true"  
      />  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d9cd-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d9cd-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="0d9cd-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="0d9cd-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
