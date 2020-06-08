---
title: <defaultProxy> – element (nastavení sítě)
description: <defaultProxy>Prvek nastavení sítě konfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol) v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
ms.openlocfilehash: 915fdc96dbd4d417f9c9e6aa3ff96de3026491ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504599"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="2c14c-103">\<defaultProxy> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2c14c-103">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="2c14c-104">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="2c14c-104">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="2c14c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c14c-105">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c14c-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2c14c-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2c14c-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2c14c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c14c-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="2c14c-108">Attributes</span></span>  
  
|<span data-ttu-id="2c14c-109">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="2c14c-109">**Element**</span></span>|<span data-ttu-id="2c14c-110">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2c14c-110">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="2c14c-111">Určuje, zda je použit webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="2c14c-111">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="2c14c-112">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="2c14c-112">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="2c14c-113">Určuje, jestli se pro přístup k webovému proxy serveru používají výchozí přihlašovací údaje pro tohoto hostitele.</span><span class="sxs-lookup"><span data-stu-id="2c14c-113">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="2c14c-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="2c14c-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c14c-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2c14c-115">Child Elements</span></span>  
  
|<span data-ttu-id="2c14c-116">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="2c14c-116">**Element**</span></span>|<span data-ttu-id="2c14c-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2c14c-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2c14c-118">bypasslist</span><span class="sxs-lookup"><span data-stu-id="2c14c-118">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="2c14c-119">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="2c14c-119">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="2c14c-120">čipu</span><span class="sxs-lookup"><span data-stu-id="2c14c-120">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="2c14c-121">Přidá do aplikace nový modul proxy.</span><span class="sxs-lookup"><span data-stu-id="2c14c-121">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="2c14c-122">proxy</span><span class="sxs-lookup"><span data-stu-id="2c14c-122">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="2c14c-123">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="2c14c-123">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c14c-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2c14c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2c14c-125">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="2c14c-125">**Element**</span></span>|<span data-ttu-id="2c14c-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2c14c-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2c14c-127">system.net</span><span class="sxs-lookup"><span data-stu-id="2c14c-127">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="2c14c-128">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="2c14c-128">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c14c-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c14c-129">Remarks</span></span>  
 <span data-ttu-id="2c14c-130">Pokud je Element defaultProxy prázdný, použije se nastavení proxy z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="2c14c-130">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="2c14c-131">Toto chování se liší od verze 1,1 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c14c-131">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="2c14c-132">Výjimka je vyvolána, pokud prvek [modulu](module-element-network-settings.md) určuje typ, který není veřejný, typ není odvozen od <xref:System.Net.IWebProxy> třídy, došlo k výjimce z konstruktoru bez parametrů, nebo při načítání výchozího serveru proxy zadaného systémem došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="2c14c-132">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="2c14c-133"><xref:System.Exception.InnerException%2A>Vlastnost výjimky by měla obsahovat další informace o hlavní příčině chyby.</span><span class="sxs-lookup"><span data-stu-id="2c14c-133">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2c14c-134">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="2c14c-134">Configuration Files</span></span>  
 <span data-ttu-id="2c14c-135">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2c14c-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c14c-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c14c-136">Example</span></span>  
 <span data-ttu-id="2c14c-137">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy server pro místní přístup a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="2c14c-137">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c14c-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c14c-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="2c14c-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2c14c-139">Network Settings Schema</span></span>](index.md)
