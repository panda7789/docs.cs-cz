---
title: '&lt;IPv6&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: 02ac6ecb372b1e902d65d4b35ef71fbf0ac093c4
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170117"
---
# <a name="ltipv6gt-element-network-settings"></a><span data-ttu-id="cb767-102">&lt;IPv6&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="cb767-102">&lt;ipv6&gt; Element (Network Settings)</span></span>
<span data-ttu-id="cb767-103">Umožňuje Internet Protocol verze 6 (IPv6) odpovědí z zastaralé členy <xref:System.Net.Dns> třídy.</span><span class="sxs-lookup"><span data-stu-id="cb767-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="cb767-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="cb767-104">\<configuration></span></span>  
<span data-ttu-id="cb767-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cb767-105">\<system.net></span></span>  
<span data-ttu-id="cb767-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="cb767-106">\<settings></span></span>  
<span data-ttu-id="cb767-107">\<IPv6 ></span><span class="sxs-lookup"><span data-stu-id="cb767-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb767-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb767-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb767-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cb767-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cb767-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cb767-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb767-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="cb767-111">Attributes</span></span>  
  
|<span data-ttu-id="cb767-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="cb767-112">**Attribute**</span></span>|<span data-ttu-id="cb767-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cb767-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="cb767-114">Určuje, zda členové <xref:System.Net.Dns> třídy vrátit Internet Protocol verze 6 adresy (IPv6).</span><span class="sxs-lookup"><span data-stu-id="cb767-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="cb767-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="cb767-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb767-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cb767-116">Child Elements</span></span>  
 <span data-ttu-id="cb767-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="cb767-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb767-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cb767-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cb767-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="cb767-119">**Element**</span></span>|<span data-ttu-id="cb767-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cb767-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cb767-121">Nastavení</span><span class="sxs-lookup"><span data-stu-id="cb767-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="cb767-122">Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cb767-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb767-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb767-123">Remarks</span></span>  
 <span data-ttu-id="cb767-124">Toto nastavení umožňuje podporu protokolu IPv6 pro zastaralé členy <xref:System.Net.Dns> třídy: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, a <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb767-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="cb767-125">Pro ostatní členy <xref:System.Net?displayProperty=nameWithType> obor názvů, IPv6 adresy mohou být vráceny Pokud v operačním systému je povolen protokol IPv6.</span><span class="sxs-lookup"><span data-stu-id="cb767-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cb767-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="cb767-126">Configuration Files</span></span>  
 <span data-ttu-id="cb767-127">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="cb767-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb767-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb767-128">Example</span></span>  
 <span data-ttu-id="cb767-129">Následující příklad ukazuje, jak povolit podporu IPv6 <xref:System.Net.Dns> třídy.</span><span class="sxs-lookup"><span data-stu-id="cb767-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb767-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb767-130">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Dns?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="cb767-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="cb767-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
