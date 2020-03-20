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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154553"
---
# <a name="systemnet-element-network-settings"></a><span data-ttu-id="5b9a9-102">\<system.Net> element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="5b9a9-102">\<system.Net> Element (Network Settings)</span></span>
<span data-ttu-id="5b9a9-103">Obsahuje nastavení, která určují, jak se rozhraní .NET Framework připojuje k síti.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-103">Contains settings that specify how the .NET Framework connects to the network.</span></span>  
  
[<span data-ttu-id="5b9a9-104">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="5b9a9-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="5b9a9-105">&nbsp;&nbsp;**\<system.net>**</span><span class="sxs-lookup"><span data-stu-id="5b9a9-105">&nbsp;&nbsp;**\<system.net>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b9a9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b9a9-106">Syntax</span></span>  
  
```xml  
<system.net>
</system.net>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b9a9-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5b9a9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5b9a9-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b9a9-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="5b9a9-109">Attributes</span></span>  
 <span data-ttu-id="5b9a9-110">Žádné.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5b9a9-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5b9a9-111">Child Elements</span></span>  
  
|<span data-ttu-id="5b9a9-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="5b9a9-112">**Element**</span></span>|<span data-ttu-id="5b9a9-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="5b9a9-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5b9a9-114">autentizační moduly</span><span class="sxs-lookup"><span data-stu-id="5b9a9-114">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="5b9a9-115">Určuje moduly používané k ověřování požadavků sítě Internet.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-115">Specifies modules used to authenticate Internet requests.</span></span>|  
|[<span data-ttu-id="5b9a9-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="5b9a9-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="5b9a9-117">Určuje maximální počet připojení k hostiteli sítě Internet.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-117">Specifies the maximum number of connections to an Internet host.</span></span>|  
|[<span data-ttu-id="5b9a9-118">výchozí proxy</span><span class="sxs-lookup"><span data-stu-id="5b9a9-118">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="5b9a9-119">Konfiguruje proxy server HTTP (HTTP).</span><span class="sxs-lookup"><span data-stu-id="5b9a9-119">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
|[<span data-ttu-id="5b9a9-120">mailNastavení</span><span class="sxs-lookup"><span data-stu-id="5b9a9-120">mailSettings</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="5b9a9-121">Konfiguruje možnosti odesílání pošty protokolu SMTP (SMTP) protokolu SMTP.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-121">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
|[<span data-ttu-id="5b9a9-122">requestCaching</span><span class="sxs-lookup"><span data-stu-id="5b9a9-122">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="5b9a9-123">Řídí mechanismus ukládání do mezipaměti pro síťové požadavky.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-123">Controls the caching mechanism for network requests.</span></span>|  
|[<span data-ttu-id="5b9a9-124">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="5b9a9-124">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="5b9a9-125">Konfiguruje základní možnosti sítě pro třídy v <xref:System.Net> a souvisejícípodřízené názvobory.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-125">Configures basic network options for classes in the <xref:System.Net> and related child namespaces.</span></span>|  
|[<span data-ttu-id="5b9a9-126">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="5b9a9-126">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="5b9a9-127">Určuje moduly, které mají být používány k vyžádání informací od hostitelů v Síti Internet.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-127">Specifies modules to use to request information from Internet hosts.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5b9a9-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5b9a9-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5b9a9-129">**Element**</span><span class="sxs-lookup"><span data-stu-id="5b9a9-129">**Element**</span></span>|<span data-ttu-id="5b9a9-130">**Popis**</span><span class="sxs-lookup"><span data-stu-id="5b9a9-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5b9a9-131">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="5b9a9-131">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="5b9a9-132">Obsahuje nastavení pro všechny obory názvů.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-132">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b9a9-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b9a9-133">Remarks</span></span>  
 <span data-ttu-id="5b9a9-134">Prvek [ \<system.net>](system-net-element-network-settings.md) obsahuje nastavení <xref:System.Net> pro třídy v a související podřízené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-134">The [\<system.net>](system-net-element-network-settings.md) element contains settings for classes in the <xref:System.Net> and related child namespaces.</span></span> <span data-ttu-id="5b9a9-135">Nastavení konfigurují ověřovací moduly, správu připojení, nastavení pošty, proxy server a moduly požadavků na Internet pro příjem informací z hostitelů sítě Internet.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-135">The settings configure authentication modules, connection management, mail settings, the proxy server, and Internet request modules for receiving information from Internet hosts.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b9a9-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b9a9-136">Example</span></span>  
 <span data-ttu-id="5b9a9-137">Následující příklad ukazuje typickou <xref:System.Net> konfiguraci používanou třídami.</span><span class="sxs-lookup"><span data-stu-id="5b9a9-137">The following example shows a typical configuration used by <xref:System.Net> classes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b9a9-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b9a9-138">See also</span></span>

- [<span data-ttu-id="5b9a9-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="5b9a9-139">Network Settings Schema</span></span>](index.md)
