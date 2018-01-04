---
title: "&lt;defaultProxy –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultProxy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy
helpviewer_keywords:
- defaultProxy element
- <defaultProxy> element
ms.assetid: 9d663c4b-07b4-4f6f-9b12-efbd3630354f
caps.latest.revision: "21"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d0b09f5c845fc9a18c2a1dd919272c2924478eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultproxygt-element-network-settings"></a><span data-ttu-id="1fff0-102">&lt;defaultProxy –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="1fff0-102">&lt;defaultProxy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="1fff0-103">Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="1fff0-103">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>  
  
 <span data-ttu-id="1fff0-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="1fff0-104">\<configuration></span></span>  
<span data-ttu-id="1fff0-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="1fff0-105">\<system.net></span></span>  
<span data-ttu-id="1fff0-106">\<defaultProxy – ></span><span class="sxs-lookup"><span data-stu-id="1fff0-106">\<defaultProxy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fff0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fff0-107">Syntax</span></span>  
  
```xml  
      <defaultProxy  
        enabled="true|false"  
        useDefaultCredentials="true|false">  
           <bypasslist> … </bypasslist>  
           <proxy> … </proxy>  
           <module> … </module>  
      </defaultProxy>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fff0-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1fff0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1fff0-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1fff0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fff0-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="1fff0-110">Attributes</span></span>  
  
|<span data-ttu-id="1fff0-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="1fff0-111">**Element**</span></span>|<span data-ttu-id="1fff0-112">**Popis**</span><span class="sxs-lookup"><span data-stu-id="1fff0-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="1fff0-113">Určuje, jestli se používá webový proxy server.</span><span class="sxs-lookup"><span data-stu-id="1fff0-113">Specifies whether a web proxy is used.</span></span> <span data-ttu-id="1fff0-114">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="1fff0-114">The default value is `true`.</span></span>|  
|`useDefaultCredentials`|<span data-ttu-id="1fff0-115">Určuje, jestli jsou pro přístup k proxy serveru webové používá výchozí pověření pro tohoto hostitele.</span><span class="sxs-lookup"><span data-stu-id="1fff0-115">Specifies whether the default credentials for this host are used to access the web proxy.</span></span> <span data-ttu-id="1fff0-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1fff0-116">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fff0-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1fff0-117">Child Elements</span></span>  
  
|<span data-ttu-id="1fff0-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="1fff0-118">**Element**</span></span>|<span data-ttu-id="1fff0-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="1fff0-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1fff0-120">bypasslist –</span><span class="sxs-lookup"><span data-stu-id="1fff0-120">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="1fff0-121">Poskytuje sadu regulární výrazy, které popisují adresy, které nepoužívají proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="1fff0-121">Provides a set of regular expressions that describe addresses that do not use the proxy.</span></span>|  
|[<span data-ttu-id="1fff0-122">modul</span><span class="sxs-lookup"><span data-stu-id="1fff0-122">module</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md)|<span data-ttu-id="1fff0-123">Přidá nový modul proxy serveru k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1fff0-123">Adds a new proxy module to the application.</span></span>|  
|[<span data-ttu-id="1fff0-124">proxy server</span><span class="sxs-lookup"><span data-stu-id="1fff0-124">proxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md)|<span data-ttu-id="1fff0-125">Definuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="1fff0-125">Defines a proxy server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1fff0-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1fff0-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1fff0-127">**Element**</span><span class="sxs-lookup"><span data-stu-id="1fff0-127">**Element**</span></span>|<span data-ttu-id="1fff0-128">**Popis**</span><span class="sxs-lookup"><span data-stu-id="1fff0-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1fff0-129">System.NET</span><span class="sxs-lookup"><span data-stu-id="1fff0-129">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="1fff0-130">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="1fff0-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fff0-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fff0-131">Remarks</span></span>  
 <span data-ttu-id="1fff0-132">Pokud defaultProxy – element není prázdný, použije se nastavení proxy serveru z Internet Exploreru.</span><span class="sxs-lookup"><span data-stu-id="1fff0-132">If the defaultProxy element is empty, the proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="1fff0-133">Toto chování se liší od rozhraní .NET Framework verze 1.1.</span><span class="sxs-lookup"><span data-stu-id="1fff0-133">This behavior is different from version 1.1 of the .NET Framework.</span></span>  
  
 <span data-ttu-id="1fff0-134">Je vyvolána výjimka, pokud [modulu](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element určuje typ neveřejný, typ není odvozování z <xref:System.Net.IWebProxy> třídu, došlo k výjimce z výchozí konstruktor tohoto objektu, nebo došlo k výjimce při načítání systému zadat výchozí proxy server.</span><span class="sxs-lookup"><span data-stu-id="1fff0-134">An exception is thrown if the [module](../../../../../docs/framework/configure-apps/file-schema/network/module-element-network-settings.md) element specifies a non-public type, the type is not deriving from the <xref:System.Net.IWebProxy> class, an exception from the default constructor of this object occurred, or an exception occurred while retrieving the system-specified default proxy.</span></span> <span data-ttu-id="1fff0-135"><xref:System.Exception.InnerException%2A> Vlastnost výjimky by měl mít další informace o hlavních příčin této chyby.</span><span class="sxs-lookup"><span data-stu-id="1fff0-135">The <xref:System.Exception.InnerException%2A> property on the exception should have more information about the root cause of the error.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="1fff0-136">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="1fff0-136">Configuration Files</span></span>  
 <span data-ttu-id="1fff0-137">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="1fff0-137">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fff0-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fff0-138">Example</span></span>  
 <span data-ttu-id="1fff0-139">Následující příklad používá výchozí hodnoty z proxy serveru aplikace Internet Explorer, určuje adresu proxy serveru a obchází proxy pro místní přístup a contoso.com.</span><span class="sxs-lookup"><span data-stu-id="1fff0-139">The following example uses the defaults from the Internet Explorer proxy, specifies the proxy address, and bypasses the proxy for local access and contoso.com.</span></span>  
  
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
        <add address="[a-z]+\.contoso\.com" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fff0-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fff0-140">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="1fff0-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="1fff0-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
