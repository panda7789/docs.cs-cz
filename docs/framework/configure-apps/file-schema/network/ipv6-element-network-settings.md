---
title: <ipv6> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/ipv6
- http://schemas.microsoft.com/.NetConfiguration/v2.0#ipv6
helpviewer_keywords:
- <ipv6> element
- ipv6 element
ms.assetid: 10b79aef-327b-4718-a892-e11f55e4d169
ms.openlocfilehash: d89c2e2c6943aca38f8a71092ba3121447a77574
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664098"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="ebee5-102">\<> – element IPv6 (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="ebee5-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="ebee5-103">Povoluje odpovědi na Internet Protocol verze 6 (IPv6) od zastaralých členů <xref:System.Net.Dns> třídy.</span><span class="sxs-lookup"><span data-stu-id="ebee5-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
 <span data-ttu-id="ebee5-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="ebee5-104">\<configuration></span></span>  
<span data-ttu-id="ebee5-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ebee5-105">\<system.net></span></span>  
<span data-ttu-id="ebee5-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="ebee5-106">\<settings></span></span>  
<span data-ttu-id="ebee5-107">\<ipv6></span><span class="sxs-lookup"><span data-stu-id="ebee5-107">\<ipv6></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebee5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebee5-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebee5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ebee5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ebee5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ebee5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebee5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ebee5-111">Attributes</span></span>  
  
|<span data-ttu-id="ebee5-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="ebee5-112">**Attribute**</span></span>|<span data-ttu-id="ebee5-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="ebee5-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="ebee5-114">Určuje, zda členové <xref:System.Net.Dns> třídy vracejí adresy Internet Protocol verze 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="ebee5-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="ebee5-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="ebee5-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebee5-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ebee5-116">Child Elements</span></span>  
 <span data-ttu-id="ebee5-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="ebee5-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebee5-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ebee5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ebee5-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="ebee5-119">**Element**</span></span>|<span data-ttu-id="ebee5-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="ebee5-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ebee5-121">možnost</span><span class="sxs-lookup"><span data-stu-id="ebee5-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="ebee5-122">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ebee5-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebee5-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ebee5-123">Remarks</span></span>  
 <span data-ttu-id="ebee5-124">Toto <xref:System.Net.Dns> nastavení povoluje podporu protokolu IPv6 pro zastaralé členy třídy: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>a <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebee5-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="ebee5-125">Pokud je v operačním systému <xref:System.Net?displayProperty=nameWithType> povolený protokol IPv6, můžou se u ostatních členů oboru názvů vracet IPv6 adresy.</span><span class="sxs-lookup"><span data-stu-id="ebee5-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ebee5-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="ebee5-126">Configuration Files</span></span>  
 <span data-ttu-id="ebee5-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ebee5-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebee5-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebee5-128">Example</span></span>  
 <span data-ttu-id="ebee5-129">Následující příklad ukazuje, jak povolit podporu protokolu IPv6 pro <xref:System.Net.Dns> třídu.</span><span class="sxs-lookup"><span data-stu-id="ebee5-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebee5-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebee5-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ebee5-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="ebee5-131">Network Settings Schema</span></span>](index.md)
