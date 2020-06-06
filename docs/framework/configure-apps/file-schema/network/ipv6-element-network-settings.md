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
ms.openlocfilehash: c16949171d082bd02abb0a02db83c2e71c2f17df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088135"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="03343-102">\<ipv6> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="03343-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="03343-103">Povoluje odpovědi na Internet Protocol verze 6 (IPv6) od zastaralých členů <xref:System.Net.Dns> třídy.</span><span class="sxs-lookup"><span data-stu-id="03343-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**

## <a name="syntax"></a><span data-ttu-id="03343-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03343-104">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03343-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03343-105">Attributes and Elements</span></span>  
 <span data-ttu-id="03343-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03343-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03343-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="03343-107">Attributes</span></span>  
  
|<span data-ttu-id="03343-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="03343-108">**Attribute**</span></span>|<span data-ttu-id="03343-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="03343-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="03343-110">Určuje, zda členové <xref:System.Net.Dns> třídy vracejí adresy Internet Protocol verze 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="03343-110">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="03343-111">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="03343-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03343-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03343-112">Child Elements</span></span>  
 <span data-ttu-id="03343-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="03343-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03343-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03343-114">Parent Elements</span></span>  
  
|<span data-ttu-id="03343-115">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="03343-115">**Element**</span></span>|<span data-ttu-id="03343-116">**Popis**</span><span class="sxs-lookup"><span data-stu-id="03343-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="03343-117">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="03343-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="03343-118">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="03343-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03343-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03343-119">Remarks</span></span>  
 <span data-ttu-id="03343-120">Toto nastavení povoluje podporu protokolu IPv6 pro zastaralé členy <xref:System.Net.Dns> třídy: <xref:System.Net.Dns.BeginGetHostByName%2A> , <xref:System.Net.Dns.BeginResolve%2A> , <xref:System.Net.Dns.EndGetHostByName%2A> , <xref:System.Net.Dns.EndResolve%2A> , <xref:System.Net.Dns.GetHostByAddress%2A> , <xref:System.Net.Dns.GetHostByName%2A> a <xref:System.Net.Dns.Resolve%2A> .</span><span class="sxs-lookup"><span data-stu-id="03343-120">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="03343-121"><xref:System.Net?displayProperty=nameWithType>Pokud je v operačním systému povolený protokol IPv6, můžou se u ostatních členů oboru názvů vracet IPv6 adresy.</span><span class="sxs-lookup"><span data-stu-id="03343-121">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="03343-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="03343-122">Configuration Files</span></span>  
 <span data-ttu-id="03343-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="03343-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="03343-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="03343-124">Example</span></span>  
 <span data-ttu-id="03343-125">Následující příklad ukazuje, jak povolit podporu protokolu IPv6 pro <xref:System.Net.Dns> třídu.</span><span class="sxs-lookup"><span data-stu-id="03343-125">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="03343-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="03343-126">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="03343-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="03343-127">Network Settings Schema</span></span>](index.md)
