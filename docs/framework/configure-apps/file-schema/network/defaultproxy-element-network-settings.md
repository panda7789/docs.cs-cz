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
ms.openlocfilehash: 0945629c1395917bc1cf825f2ba84d20afa99957
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698211"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="e0fc4-102">\<element > defaultProxy (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e0fc4-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="e0fc4-103">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="e0fc4-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[<span data-ttu-id="e0fc4-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="e0fc4-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e0fc4-105">&nbsp;&nbsp;[ **\<System. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e0fc4-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="e0fc4-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<defaultProxy >**</span><span class="sxs-lookup"><span data-stu-id="e0fc4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0fc4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0fc4-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0fc4-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e0fc4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e0fc4-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0fc4-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e0fc4-110">Attributes</span></span>  
  
|<span data-ttu-id="e0fc4-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="e0fc4-111">**Element**</span></span>|<span data-ttu-id="e0fc4-112">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e0fc4-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="e0fc4-113">Určuje, zda je použit webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="e0fc4-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="e0fc4-115">Určuje, jestli se pro přístup k webovému proxy serveru používají výchozí přihlašovací údaje pro tohoto hostitele.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="e0fc4-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0fc4-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e0fc4-117">Child Elements</span></span>  
  
|<span data-ttu-id="e0fc4-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="e0fc4-118">**Element**</span></span>|<span data-ttu-id="e0fc4-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e0fc4-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e0fc4-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="e0fc4-120">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="e0fc4-121">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="e0fc4-122">module</span><span class="sxs-lookup"><span data-stu-id="e0fc4-122">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="e0fc4-123">Přidá do aplikace nový modul proxy.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="e0fc4-124">proxy</span><span class="sxs-lookup"><span data-stu-id="e0fc4-124">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="e0fc4-125">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0fc4-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e0fc4-126">Parent Elements</span></span>  
  
|<span data-ttu-id="e0fc4-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="e0fc4-127">**Element**</span></span>|<span data-ttu-id="e0fc4-128">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e0fc4-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e0fc4-129">system.net</span><span class="sxs-lookup"><span data-stu-id="e0fc4-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="e0fc4-130">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0fc4-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0fc4-131">Remarks</span></span>  
 <span data-ttu-id="e0fc4-132">Pokud je Element defaultProxy prázdný, použije se nastavení proxy z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="e0fc4-133">Toto chování se liší od verze 1,1 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="e0fc4-134">Výjimka je vyvolána, pokud prvek [modulu](module-element-network-settings.md) určuje typ, který není veřejný, typ není odvozen od třídy <xref:System.Net.IWebProxy>, došlo k výjimce z konstruktoru bez parametrů, nebo při načítání výchozího serveru proxy zadaného systémem došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-134">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="e0fc4-135">Vlastnost <xref:System.Exception.InnerException%2A> výjimky by měla obsahovat další informace o hlavní příčině chyby.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e0fc4-136">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="e0fc4-136">Configuration Files</span></span>  
 <span data-ttu-id="e0fc4-137">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e0fc4-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0fc4-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0fc4-138">Example</span></span>  
 <span data-ttu-id="e0fc4-139">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy server pro místní přístup a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="e0fc4-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0fc4-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0fc4-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e0fc4-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e0fc4-141">Network Settings Schema</span></span>](index.md)
