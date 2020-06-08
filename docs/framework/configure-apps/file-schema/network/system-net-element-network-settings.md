---
title: <system.Net> – element (nastavení sítě)
description: Prvek <system.Net> nastavení sítě obsahuje nastavení, která určují, jak se .NET Framework připojí k možnostem sítě v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 9f18c7a3586948c03391d609f437e216a91bc27f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504482"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="abb3d-103">\<system.Net> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="abb3d-103">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="abb3d-104">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="abb3d-104">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="abb3d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abb3d-105">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abb3d-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="abb3d-106">Attributes and Elements</span></span>  
 <span data-ttu-id="abb3d-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="abb3d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abb3d-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="abb3d-108">Attributes</span></span>  
 <span data-ttu-id="abb3d-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="abb3d-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="abb3d-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="abb3d-110">Child Elements</span></span>  
  
|<span data-ttu-id="abb3d-111">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="abb3d-111">**Element**</span></span>|<span data-ttu-id="abb3d-112">**Popis**</span><span class="sxs-lookup"><span data-stu-id="abb3d-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="abb3d-113">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="abb3d-113">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="abb3d-114">Určuje moduly používané pro ověřování internetových požadavků.</span><span class="sxs-lookup"><span data-stu-id="abb3d-114">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="abb3d-115">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="abb3d-115">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="abb3d-116">Určuje maximální počet připojení k hostiteli v Internetu.</span><span class="sxs-lookup"><span data-stu-id="abb3d-116">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="abb3d-117">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="abb3d-117">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="abb3d-118">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="abb3d-118">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="abb3d-119">mailSettings</span><span class="sxs-lookup"><span data-stu-id="abb3d-119">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="abb3d-120">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="abb3d-120">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="abb3d-121">requestCaching</span><span class="sxs-lookup"><span data-stu-id="abb3d-121">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="abb3d-122">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="abb3d-122">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="abb3d-123">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="abb3d-123">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="abb3d-124">Konfiguruje základní možnosti sítě pro třídy v <xref:System.Net> souvisejících podřízených oborech názvů a.</span><span class="sxs-lookup"><span data-stu-id="abb3d-124">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="abb3d-125">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="abb3d-125">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="abb3d-126">Určuje moduly, které se použijí k vyžádání informací od hostitelů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="abb3d-126">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="abb3d-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="abb3d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="abb3d-128">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="abb3d-128">**Element**</span></span>|<span data-ttu-id="abb3d-129">**Popis**</span><span class="sxs-lookup"><span data-stu-id="abb3d-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="abb3d-130">rozšířeného</span><span class="sxs-lookup"><span data-stu-id="abb3d-130">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="abb3d-131">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="abb3d-131">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abb3d-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abb3d-132">Remarks</span></span>  
 <span data-ttu-id="abb3d-133">[\<system.net>](system-net-element-network-settings.md)Element obsahuje nastavení pro třídy v <xref:System.Net> souvisejících podřízených oborech názvů a.</span><span class="sxs-lookup"><span data-stu-id="abb3d-133">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="abb3d-134">Nastavení konfigurovat ověřovací moduly, správu připojení, nastavení pošty, proxy server a moduly internetových požadavků pro příjem informací z internetových hostitelů.</span><span class="sxs-lookup"><span data-stu-id="abb3d-134">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abb3d-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="abb3d-135">Example</span></span>  
 <span data-ttu-id="abb3d-136">Následující příklad ukazuje typickou konfiguraci, kterou používají <xref:System.Net> třídy.</span><span class="sxs-lookup"><span data-stu-id="abb3d-136">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient" />  
      <add type="System.Net.NegotiateClient" />  
      <add type="System.Net.KerberosClient" />  
      <add type="System.Net.NtlmClient" />  
      <add type="System.Net.BasicClient" />  
    </authenticationModules>  
    <connectionManagement>  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
    <defaultProxy>  
      <proxy  
        usesystemdefault="true"  
        bypassonlocal="true"  
      />  
    </defaultProxy>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="https"  
           type="System.Net.HttpRequestCreator"  
      />  
      <add prefix="file"  
           type="System.Net.FileWebRequestCreator"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="abb3d-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abb3d-137">See also</span></span>

- [<span data-ttu-id="abb3d-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="abb3d-138">Network Settings Schema</span></span>](index.md)
