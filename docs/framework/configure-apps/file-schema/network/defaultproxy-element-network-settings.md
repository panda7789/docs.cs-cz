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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698211"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="b960c-102">\<defaultProxy> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b960c-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="b960c-103">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="b960c-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultProxy>**  
  
## <a name="syntax"></a><span data-ttu-id="b960c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b960c-104">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b960c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b960c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b960c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b960c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b960c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b960c-107">Attributes</span></span>  
  
|<span data-ttu-id="b960c-108">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="b960c-108">**Element**</span></span>|<span data-ttu-id="b960c-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b960c-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="b960c-110">Určuje, zda je použit webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="b960c-110">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="b960c-111">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="b960c-111">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="b960c-112">Určuje, jestli se pro přístup k webovému proxy serveru používají výchozí přihlašovací údaje pro tohoto hostitele.</span><span class="sxs-lookup"><span data-stu-id="b960c-112">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="b960c-113">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b960c-113">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b960c-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b960c-114">Child Elements</span></span>  
  
|<span data-ttu-id="b960c-115">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="b960c-115">**Element**</span></span>|<span data-ttu-id="b960c-116">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b960c-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b960c-117">bypasslist</span><span class="sxs-lookup"><span data-stu-id="b960c-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="b960c-118">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="b960c-118">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="b960c-119">čipu</span><span class="sxs-lookup"><span data-stu-id="b960c-119">module</span></span>](module-element-network-settings.md)|<span data-ttu-id="b960c-120">Přidá do aplikace nový modul proxy.</span><span class="sxs-lookup"><span data-stu-id="b960c-120">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="b960c-121">proxy</span><span class="sxs-lookup"><span data-stu-id="b960c-121">proxy</span></span>](proxy-element-network-settings.md)|<span data-ttu-id="b960c-122">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="b960c-122">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b960c-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b960c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b960c-124">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="b960c-124">**Element**</span></span>|<span data-ttu-id="b960c-125">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b960c-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b960c-126">system.net</span><span class="sxs-lookup"><span data-stu-id="b960c-126">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="b960c-127">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="b960c-127">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b960c-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b960c-128">Remarks</span></span>  
 <span data-ttu-id="b960c-129">Pokud je Element defaultProxy prázdný, použije se nastavení proxy z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="b960c-129">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="b960c-130">Toto chování se liší od verze 1,1 .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b960c-130">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b960c-131">Výjimka je vyvolána, pokud prvek [modulu](module-element-network-settings.md) určuje typ, který není veřejný, typ není odvozen od <xref:System.Net.IWebProxy> třídy, došlo k výjimce z konstruktoru bez parametrů, nebo při načítání výchozího serveru proxy zadaného systémem došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="b960c-131">An exception is thrown if the [module](module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the parameterless constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="b960c-132"><xref:System.Exception.InnerException%2A>Vlastnost výjimky by měla obsahovat další informace o hlavní příčině chyby.</span><span class="sxs-lookup"><span data-stu-id="b960c-132">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b960c-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="b960c-133">Configuration Files</span></span>  
 <span data-ttu-id="b960c-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b960c-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b960c-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="b960c-135">Example</span></span>  
 <span data-ttu-id="b960c-136">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy server pro místní přístup a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="b960c-136">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b960c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="b960c-137">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="b960c-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b960c-138">Network Settings Schema</span></span>](index.md)
