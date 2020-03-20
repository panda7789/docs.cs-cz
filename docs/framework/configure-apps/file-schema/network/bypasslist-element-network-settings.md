---
title: <bypasslist> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154943"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="f2c15-102">\<bypasslist> Element (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f2c15-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="f2c15-103">Obsahuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="f2c15-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="f2c15-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f2c15-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f2c15-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f2c15-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="f2c15-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f2c15-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="f2c15-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span><span class="sxs-lookup"><span data-stu-id="f2c15-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f2c15-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2c15-108">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2c15-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f2c15-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f2c15-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f2c15-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2c15-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f2c15-111">Attributes</span></span>  
 <span data-ttu-id="f2c15-112">Žádné.</span><span class="sxs-lookup"><span data-stu-id="f2c15-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2c15-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f2c15-113">Child Elements</span></span>  
  
|<span data-ttu-id="f2c15-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="f2c15-114">**Element**</span></span>|<span data-ttu-id="f2c15-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="f2c15-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f2c15-116">Přidat</span><span class="sxs-lookup"><span data-stu-id="f2c15-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="f2c15-117">Přidá adresu IP nebo název DNS do seznamu obejití serveru proxy.</span><span class="sxs-lookup"><span data-stu-id="f2c15-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="f2c15-118">Jasné</span><span class="sxs-lookup"><span data-stu-id="f2c15-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="f2c15-119">Vymaže seznam bypass.</span><span class="sxs-lookup"><span data-stu-id="f2c15-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="f2c15-120">Odebrat</span><span class="sxs-lookup"><span data-stu-id="f2c15-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="f2c15-121">Odebere adresu IP nebo název DNS ze seznamu obejití serveru proxy.</span><span class="sxs-lookup"><span data-stu-id="f2c15-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2c15-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f2c15-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f2c15-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="f2c15-123">**Element**</span></span>|<span data-ttu-id="f2c15-124">**Popis**</span><span class="sxs-lookup"><span data-stu-id="f2c15-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f2c15-125">výchozí proxy</span><span class="sxs-lookup"><span data-stu-id="f2c15-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="f2c15-126">Konfiguruje proxy server HTTP (HTTP).</span><span class="sxs-lookup"><span data-stu-id="f2c15-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2c15-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2c15-127">Remarks</span></span>  
 <span data-ttu-id="f2c15-128">Seznam obejití obsahuje regulární <xref:System.Net.WebRequest> výrazy, které popisují identifikátory URI, které instancí přistupují přímo namísto prostřednictvím proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="f2c15-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="f2c15-129">Při zadávání regulárního výrazu pro tento prvek byste měli být opatrní.</span><span class="sxs-lookup"><span data-stu-id="f2c15-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="f2c15-130">Regulární výraz "[a-z]+\\\\.contoso .com" odpovídá libovolnému hostiteli v contoso.com doméně, ale také odpovídá libovolnému hostiteli v contoso.com.cpandl.com doméně.</span><span class="sxs-lookup"><span data-stu-id="f2c15-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="f2c15-131">Chcete-li porovnat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z]+\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="f2c15-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="f2c15-132">Další informace o regulárních výrazech naleznete v tématu . [Regulární výrazy rozhraní .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f2c15-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f2c15-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="f2c15-133">Configuration Files</span></span>  
 <span data-ttu-id="f2c15-134">Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f2c15-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2c15-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2c15-135">Example</span></span>  
 <span data-ttu-id="f2c15-136">Následující příklad přidá dvě adresy do seznamu bypass.</span><span class="sxs-lookup"><span data-stu-id="f2c15-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="f2c15-137">První obchází proxy servery pro všechny servery v doméně contoso.com; druhý obchází proxy server pro všechny servery, jejichž IP adresy začínají 192.168.</span><span class="sxs-lookup"><span data-stu-id="f2c15-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2c15-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2c15-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f2c15-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="f2c15-139">Network Settings Schema</span></span>](index.md)
