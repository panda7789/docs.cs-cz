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
ms.openlocfilehash: ce08dadb0fb7b986c0573b1514f9ecbbe2961c3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674568"
---
# <a name="defaultproxy-element-network-settings"></a><span data-ttu-id="c4344-102">\<defaultProxy > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="c4344-102">\<defaultProxy> Element (Network Settings)</span></span>
<span data-ttu-id="c4344-103">Konfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="c4344-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="c4344-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c4344-104">\<configuration></span></span>  
<span data-ttu-id="c4344-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c4344-105">\<system.net></span></span>  
<span data-ttu-id="c4344-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="c4344-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4344-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4344-107">Syntax</span></span>  
  
```xml  
<defaultProxy  
  enabled="true|false"  
  useDefaultCredentials="true|false">  
    <bypasslist>...</bypasslist>  
    <proxy>...</proxy>  
    <module>...</module>  
</defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4344-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c4344-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c4344-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c4344-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4344-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c4344-110">Attributes</span></span>  
  
|<span data-ttu-id="c4344-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="c4344-111">**Element**</span></span>|<span data-ttu-id="c4344-112">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c4344-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="c4344-113">Určuje, zda se používá webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="c4344-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="c4344-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="c4344-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="c4344-115">Určuje, zda výchozí přihlašovací údaje pro tohoto hostitele se používají pro přístup webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="c4344-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="c4344-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="c4344-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4344-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c4344-117">Child Elements</span></span>  
  
|<span data-ttu-id="c4344-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="c4344-118">**Element**</span></span>|<span data-ttu-id="c4344-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c4344-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c4344-120">bypasslist</span><span class="sxs-lookup"><span data-stu-id="c4344-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="c4344-121">Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="c4344-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="c4344-122">module</span><span class="sxs-lookup"><span data-stu-id="c4344-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="c4344-123">Přidá nový modul proxy serveru do aplikace.</span><span class="sxs-lookup"><span data-stu-id="c4344-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="c4344-124">proxy</span><span class="sxs-lookup"><span data-stu-id="c4344-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="c4344-125">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="c4344-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4344-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c4344-126">Parent Elements</span></span>  
  
|<span data-ttu-id="c4344-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="c4344-127">**Element**</span></span>|<span data-ttu-id="c4344-128">**Popis**</span><span class="sxs-lookup"><span data-stu-id="c4344-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c4344-129">system.net</span><span class="sxs-lookup"><span data-stu-id="c4344-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="c4344-130">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="c4344-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4344-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4344-131">Remarks</span></span>  
 <span data-ttu-id="c4344-132">Pokud defaultProxy – element je prázdný, použije se nastavení proxy serveru z aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="c4344-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="c4344-133">Toto chování se liší od verze 1.1 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4344-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="c4344-134">Pokud je vyvolána výjimka [modulu](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) prvek určuje neveřejný typ, typ není odvozený od <xref:System.Net.IWebProxy> došlo k výjimce z výchozího konstruktoru tohoto objektu třídy, nebo došlo k výjimce při načítání systému zadat výchozí proxy server.</span><span class="sxs-lookup"><span data-stu-id="c4344-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the default constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="c4344-135"><xref:System.Exception.InnerException%2A> Vlastnosti výjimky by měl mít další informace o hlavní příčinu chyby.</span><span class="sxs-lookup"><span data-stu-id="c4344-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c4344-136">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="c4344-136">Configuration Files</span></span>  
 <span data-ttu-id="c4344-137">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c4344-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4344-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4344-138">Example</span></span>  
 <span data-ttu-id="c4344-139">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy pro místní přístup a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="c4344-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4344-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4344-140">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="c4344-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="c4344-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
