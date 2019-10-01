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
ms.openlocfilehash: bf04b16682c2c1bc677fecbd6dc966090c77e1da
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698135"
---
# <a name="ipv6-element-network-settings"></a><span data-ttu-id="74d87-102">@no__t – element > 0ipv6 (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="74d87-102">\<ipv6> Element (Network Settings)</span></span>
<span data-ttu-id="74d87-103">Povoluje odpovědi na Internet Protocol verze 6 (IPv6) od zastaralých členů třídy <xref:System.Net.Dns>.</span><span class="sxs-lookup"><span data-stu-id="74d87-103">Enables Internet Protocol version 6 (IPv6) responses from obsolete members of the <xref:System.Net.Dns> class.</span></span>  
  
[<span data-ttu-id="74d87-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="74d87-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="74d87-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="74d87-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="74d87-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="74d87-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="74d87-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<ipv6 >**</span><span class="sxs-lookup"><span data-stu-id="74d87-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ipv6>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74d87-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74d87-108">Syntax</span></span>  
  
```xml  
<ipv6  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74d87-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74d87-109">Attributes and Elements</span></span>  
 <span data-ttu-id="74d87-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74d87-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74d87-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="74d87-111">Attributes</span></span>  
  
|<span data-ttu-id="74d87-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="74d87-112">**Attribute**</span></span>|<span data-ttu-id="74d87-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="74d87-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`enabled`|<span data-ttu-id="74d87-114">Určuje, zda členové třídy <xref:System.Net.Dns> vracejí adresy Internet Protocol verze 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="74d87-114">Specifies whether members of the <xref:System.Net.Dns> class return Internet Protocol version 6 (IPv6) addresses.</span></span> <span data-ttu-id="74d87-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="74d87-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74d87-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74d87-116">Child Elements</span></span>  
 <span data-ttu-id="74d87-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="74d87-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74d87-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74d87-118">Parent Elements</span></span>  
  
|<span data-ttu-id="74d87-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="74d87-119">**Element**</span></span>|<span data-ttu-id="74d87-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="74d87-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="74d87-121">možnost</span><span class="sxs-lookup"><span data-stu-id="74d87-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="74d87-122">Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="74d87-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74d87-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74d87-123">Remarks</span></span>  
 <span data-ttu-id="74d87-124">Toto nastavení umožňuje podporu protokolu IPv6 pro zastaralé členy třídy <xref:System.Net.Dns>: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A> a <xref:System.Net.Dns.Resolve%2A>.</span><span class="sxs-lookup"><span data-stu-id="74d87-124">This setting enables IPv6 support for the obsolete members of the <xref:System.Net.Dns> class: <xref:System.Net.Dns.BeginGetHostByName%2A>, <xref:System.Net.Dns.BeginResolve%2A>, <xref:System.Net.Dns.EndGetHostByName%2A>, <xref:System.Net.Dns.EndResolve%2A>, <xref:System.Net.Dns.GetHostByAddress%2A>, <xref:System.Net.Dns.GetHostByName%2A>, and <xref:System.Net.Dns.Resolve%2A>.</span></span> <span data-ttu-id="74d87-125">Pokud je v operačním systému povolený protokol IPv6, můžou se u ostatních členů oboru názvů <xref:System.Net?displayProperty=nameWithType> vracet IPv6 adresy.</span><span class="sxs-lookup"><span data-stu-id="74d87-125">For other members of the <xref:System.Net?displayProperty=nameWithType> namespace, IPv6 addresses may be returned if IPv6 is enabled in the operating system.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="74d87-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="74d87-126">Configuration Files</span></span>  
 <span data-ttu-id="74d87-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="74d87-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="74d87-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="74d87-128">Example</span></span>  
 <span data-ttu-id="74d87-129">Následující příklad ukazuje, jak povolit podporu protokolu IPv6 pro třídu <xref:System.Net.Dns>.</span><span class="sxs-lookup"><span data-stu-id="74d87-129">The following example shows how to enable IPv6 support for the <xref:System.Net.Dns> class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <ipv6 enabled="true"/>  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74d87-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74d87-130">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Dns?displayProperty=nameWithType>
- <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>
- [<span data-ttu-id="74d87-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="74d87-131">Network Settings Schema</span></span>](index.md)
