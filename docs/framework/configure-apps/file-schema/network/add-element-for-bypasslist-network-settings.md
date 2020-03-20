---
title: <add> – element pro bypasslist (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155074"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="82e75-102">\<přidat> element pro bypasslist (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="82e75-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="82e75-103">Přidá adresu IP nebo název DNS do seznamu obejití serveru proxy.</span><span class="sxs-lookup"><span data-stu-id="82e75-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[<span data-ttu-id="82e75-104">**\<>konfigurace**</span><span class="sxs-lookup"><span data-stu-id="82e75-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="82e75-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="82e75-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="82e75-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="82e75-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="82e75-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="82e75-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="82e75-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="82e75-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e75-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82e75-109">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82e75-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="82e75-110">Attributes and Elements</span></span>  
 <span data-ttu-id="82e75-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="82e75-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82e75-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="82e75-112">Attributes</span></span>  
  
|<span data-ttu-id="82e75-113">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="82e75-113">**Attribute**</span></span>|<span data-ttu-id="82e75-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="82e75-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="82e75-115">**Adresu**</span><span class="sxs-lookup"><span data-stu-id="82e75-115">**address**</span></span>|<span data-ttu-id="82e75-116">Regulární výraz popisující adresu IP nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="82e75-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82e75-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="82e75-117">Child Elements</span></span>  
 <span data-ttu-id="82e75-118">Žádné.</span><span class="sxs-lookup"><span data-stu-id="82e75-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82e75-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="82e75-119">Parent Elements</span></span>  
  
|<span data-ttu-id="82e75-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="82e75-120">**Element**</span></span>|<span data-ttu-id="82e75-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="82e75-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="82e75-122">Bypasslist</span><span class="sxs-lookup"><span data-stu-id="82e75-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="82e75-123">Obsahuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="82e75-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82e75-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82e75-124">Remarks</span></span>  
 <span data-ttu-id="82e75-125">Prvek `add` vloží regulární výrazy popisující adresy IP nebo názvy serverů DNS do seznamu adres, které obcházejí proxy server.</span><span class="sxs-lookup"><span data-stu-id="82e75-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="82e75-126">Hodnota atributu `address` by měla být regulární výraz, který popisuje sadu ADRES IP nebo názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="82e75-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="82e75-127">Při zadávání regulárního výrazu pro tento prvek byste měli být opatrní.</span><span class="sxs-lookup"><span data-stu-id="82e75-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="82e75-128">Regulární výraz "[a-z]+\\\\.contoso .com" odpovídá libovolnému hostiteli v contoso.com doméně, ale také odpovídá libovolnému hostiteli v contoso.com.cpandl.com doméně.</span><span class="sxs-lookup"><span data-stu-id="82e75-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="82e75-129">Chcete-li porovnat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z]+\\.contoso\\.com$".</span><span class="sxs-lookup"><span data-stu-id="82e75-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="82e75-130">Další informace o regulárních výrazech naleznete v tématu . [Regulární výrazy rozhraní .NET Framework](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="82e75-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="82e75-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="82e75-131">Configuration Files</span></span>  
 <span data-ttu-id="82e75-132">Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="82e75-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82e75-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="82e75-133">Example</span></span>  
 <span data-ttu-id="82e75-134">Následující příklad přidá dvě adresy do seznamu bypass.</span><span class="sxs-lookup"><span data-stu-id="82e75-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="82e75-135">První obchází proxy servery pro všechny servery v doméně contoso.com; druhý obchází proxy server pro všechny servery, jejichž IP adresa začíná 192.168.</span><span class="sxs-lookup"><span data-stu-id="82e75-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82e75-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="82e75-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="82e75-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="82e75-137">Network Settings Schema</span></span>](index.md)
