---
title: <system.Net> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.Net
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.Net
helpviewer_keywords:
- system.Net element
- <system.Net> element
ms.assetid: 52de4d6c-b24d-44aa-ba7d-6b5061f1357e
ms.openlocfilehash: 810e942394c75c192e4423afe4c674ef3a2b9900
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697506"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="3b919-102">\<– element > systému .NET (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3b919-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="3b919-103">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="3b919-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[<span data-ttu-id="3b919-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="3b919-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="3b919-105">&nbsp;&nbsp; **\<System. net >**</span><span class="sxs-lookup"><span data-stu-id="3b919-105">&nbsp;&nbsp;**\<system.net>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b919-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b919-106">Syntax</span></span>  
  
```xml  
<system.net>   
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b919-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3b919-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3b919-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3b919-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b919-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="3b919-109">Attributes</span></span>  
 <span data-ttu-id="3b919-110">Žádné.</span><span class="sxs-lookup"><span data-stu-id="3b919-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3b919-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3b919-111">Child Elements</span></span>  
  
|<span data-ttu-id="3b919-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="3b919-112">**Element**</span></span>|<span data-ttu-id="3b919-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="3b919-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3b919-114">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="3b919-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="3b919-115">Určuje moduly používané pro ověřování internetových požadavků.</span><span class="sxs-lookup"><span data-stu-id="3b919-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="3b919-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="3b919-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="3b919-117">Určuje maximální počet připojení k hostiteli v Internetu.</span><span class="sxs-lookup"><span data-stu-id="3b919-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="3b919-118">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="3b919-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="3b919-119">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="3b919-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="3b919-120">mailSettings</span><span class="sxs-lookup"><span data-stu-id="3b919-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="3b919-121">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="3b919-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="3b919-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="3b919-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="3b919-123">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="3b919-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="3b919-124">možnost</span><span class="sxs-lookup"><span data-stu-id="3b919-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="3b919-125">Konfiguruje základní možnosti sítě pro třídy v <xref:System.Net> a související podřízené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="3b919-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="3b919-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="3b919-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="3b919-127">Určuje moduly, které se použijí k vyžádání informací od hostitelů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="3b919-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b919-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3b919-128">Parent Elements</span></span>  
  
|<span data-ttu-id="3b919-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="3b919-129">**Element**</span></span>|<span data-ttu-id="3b919-130">**Popis**</span><span class="sxs-lookup"><span data-stu-id="3b919-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3b919-131">rozšířeného</span><span class="sxs-lookup"><span data-stu-id="3b919-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="3b919-132">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="3b919-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b919-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b919-133">Remarks</span></span>  
 <span data-ttu-id="3b919-134">Element [\<System. net >](system-net-element-network-settings.md) obsahuje nastavení pro třídy v <xref:System.Net> a související podřízené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="3b919-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="3b919-135">Nastavení konfigurovat ověřovací moduly, správu připojení, nastavení pošty, proxy server a moduly internetových požadavků pro příjem informací z internetových hostitelů.</span><span class="sxs-lookup"><span data-stu-id="3b919-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b919-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b919-136">Example</span></span>  
 <span data-ttu-id="3b919-137">Následující příklad ukazuje typickou konfiguraci, kterou používá <xref:System.Net> třídy.</span><span class="sxs-lookup"><span data-stu-id="3b919-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b919-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b919-138">See also</span></span>

- [<span data-ttu-id="3b919-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="3b919-139">Network Settings Schema</span></span>](index.md)
