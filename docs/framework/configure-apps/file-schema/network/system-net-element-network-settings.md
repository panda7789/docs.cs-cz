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
ms.openlocfilehash: 88098f2afaad9728e38c4f9935b45f45826a0ca9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154553"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="9eccd-102">\<system.Net> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="9eccd-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="9eccd-103">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="9eccd-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.net>**  
  
## <a name="syntax"></a><span data-ttu-id="9eccd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9eccd-104">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eccd-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9eccd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9eccd-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9eccd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eccd-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="9eccd-107">Attributes</span></span>  
 <span data-ttu-id="9eccd-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="9eccd-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9eccd-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9eccd-109">Child Elements</span></span>  
  
|<span data-ttu-id="9eccd-110">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="9eccd-110">**Element**</span></span>|<span data-ttu-id="9eccd-111">**Popis**</span><span class="sxs-lookup"><span data-stu-id="9eccd-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9eccd-112">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="9eccd-112">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="9eccd-113">Určuje moduly používané pro ověřování internetových požadavků.</span><span class="sxs-lookup"><span data-stu-id="9eccd-113">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="9eccd-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="9eccd-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="9eccd-115">Určuje maximální počet připojení k hostiteli v Internetu.</span><span class="sxs-lookup"><span data-stu-id="9eccd-115">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="9eccd-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="9eccd-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="9eccd-117">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="9eccd-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="9eccd-118">mailSettings</span><span class="sxs-lookup"><span data-stu-id="9eccd-118">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="9eccd-119">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="9eccd-119">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="9eccd-120">requestCaching</span><span class="sxs-lookup"><span data-stu-id="9eccd-120">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="9eccd-121">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="9eccd-121">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="9eccd-122">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="9eccd-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="9eccd-123">Konfiguruje základní možnosti sítě pro třídy v <xref:System.Net> souvisejících podřízených oborech názvů a.</span><span class="sxs-lookup"><span data-stu-id="9eccd-123">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="9eccd-124">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="9eccd-124">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="9eccd-125">Určuje moduly, které se použijí k vyžádání informací od hostitelů v Internetu.</span><span class="sxs-lookup"><span data-stu-id="9eccd-125">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9eccd-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9eccd-126">Parent Elements</span></span>  
  
|<span data-ttu-id="9eccd-127">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="9eccd-127">**Element**</span></span>|<span data-ttu-id="9eccd-128">**Popis**</span><span class="sxs-lookup"><span data-stu-id="9eccd-128">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9eccd-129">rozšířeného</span><span class="sxs-lookup"><span data-stu-id="9eccd-129">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="9eccd-130">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="9eccd-130">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eccd-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9eccd-131">Remarks</span></span>  
 <span data-ttu-id="9eccd-132">[\<system.net>](system-net-element-network-settings.md)Element obsahuje nastavení pro třídy v <xref:System.Net> souvisejících podřízených oborech názvů a.</span><span class="sxs-lookup"><span data-stu-id="9eccd-132">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="9eccd-133">Nastavení konfigurovat ověřovací moduly, správu připojení, nastavení pošty, proxy server a moduly internetových požadavků pro příjem informací z internetových hostitelů.</span><span class="sxs-lookup"><span data-stu-id="9eccd-133">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eccd-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="9eccd-134">Example</span></span>  
 <span data-ttu-id="9eccd-135">Následující příklad ukazuje typickou konfiguraci, kterou používají <xref:System.Net> třídy.</span><span class="sxs-lookup"><span data-stu-id="9eccd-135">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9eccd-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="9eccd-136">See also</span></span>

- [<span data-ttu-id="9eccd-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="9eccd-137">Network Settings Schema</span></span>](index.md)
