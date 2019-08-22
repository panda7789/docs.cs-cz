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
ms.openlocfilehash: 7e49762ee017564734bfb2b2f7074d94b7eabe11
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659396"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="77110-102">\<defaultProxy – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="77110-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="77110-103">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="77110-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="77110-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="77110-104">\<configuration></span></span>  
<span data-ttu-id="77110-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="77110-105">\<system.net></span></span>  
<span data-ttu-id="77110-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="77110-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77110-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77110-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77110-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="77110-108">Attributes and Elements</span></span>  
 <span data-ttu-id="77110-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="77110-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77110-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="77110-110">Attributes</span></span>  
  
|<span data-ttu-id="77110-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="77110-111">**Element**</span></span>|<span data-ttu-id="77110-112">**Popis**</span><span class="sxs-lookup"><span data-stu-id="77110-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="77110-113">Určuje, zda je použit webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="77110-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="77110-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="77110-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="77110-115">Určuje, jestli se pro přístup k webovému proxy serveru používají výchozí přihlašovací údaje pro tohoto hostitele.</span><span class="sxs-lookup"><span data-stu-id="77110-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="77110-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="77110-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77110-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="77110-117">Child Elements</span></span>  
  
|<span data-ttu-id="77110-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="77110-118">**Element**</span></span>|<span data-ttu-id="77110-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="77110-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="77110-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="77110-120">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="77110-121">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="77110-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="77110-122">module</span><span class="sxs-lookup"><span data-stu-id="77110-122">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="77110-123">Přidá do aplikace nový modul proxy.</span><span class="sxs-lookup"><span data-stu-id="77110-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="77110-124">proxy</span><span class="sxs-lookup"><span data-stu-id="77110-124">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="77110-125">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="77110-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77110-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="77110-126">Parent Elements</span></span>  
  
|<span data-ttu-id="77110-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="77110-127">**Element**</span></span>|<span data-ttu-id="77110-128">**Popis**</span><span class="sxs-lookup"><span data-stu-id="77110-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="77110-129">system.net</span><span class="sxs-lookup"><span data-stu-id="77110-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="77110-130">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="77110-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77110-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77110-131">Remarks</span></span>  
 <span data-ttu-id="77110-132">Pokud je Element defaultProxy prázdný, použije se nastavení proxy z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="77110-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="77110-133">Toto chování se liší od verze 1,1 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77110-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="77110-134">Výjimka je vyvolána, pokud prvek [modulu](module-element-network-settings.md) určuje typ, který není veřejný, typ není odvozen od <xref:System.Net.IWebProxy> třídy, došlo k výjimce z konstruktoru bez parametrů tohoto objektu, nebo došlo k výjimce při načítání výchozí proxy server zadaný systémem.</span><span class="sxs-lookup"><span data-stu-id="77110-134">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="77110-135"><xref:System.Exception.InnerException%2A> Vlastnost výjimky by měla obsahovat další informace o hlavní příčině chyby.</span><span class="sxs-lookup"><span data-stu-id="77110-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="77110-136">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="77110-136">Configuration Files</span></span>  
 <span data-ttu-id="77110-137">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="77110-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77110-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="77110-138">Example</span></span>  
 <span data-ttu-id="77110-139">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy server pro místní přístup a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="77110-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77110-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77110-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="77110-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="77110-141">Network Settings Schema</span></span>](index.md)
