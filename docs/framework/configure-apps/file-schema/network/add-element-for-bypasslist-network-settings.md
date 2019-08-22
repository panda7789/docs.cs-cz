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
ms.openlocfilehash: dd8790efa14018817c9e51e688b17c22d31d482f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659575"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="11344-102">\<Přidat > element pro BypassList (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="11344-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="11344-103">Přidá IP adresu nebo název DNS do seznamu obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="11344-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="11344-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="11344-104">\<configuration></span></span>  
<span data-ttu-id="11344-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="11344-105">\<system.net></span></span>  
<span data-ttu-id="11344-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="11344-106">\<defaultProxy></span></span>  
<span data-ttu-id="11344-107">\<BypassList ></span><span class="sxs-lookup"><span data-stu-id="11344-107">\<bypasslist></span></span>  
<span data-ttu-id="11344-108">\<add></span><span class="sxs-lookup"><span data-stu-id="11344-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11344-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11344-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11344-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11344-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11344-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11344-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11344-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="11344-112">Attributes</span></span>  
  
|<span data-ttu-id="11344-113">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="11344-113">**Attribute**</span></span>|<span data-ttu-id="11344-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="11344-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="11344-115">**address**</span><span class="sxs-lookup"><span data-stu-id="11344-115">**address**</span></span>|<span data-ttu-id="11344-116">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="11344-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11344-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11344-117">Child Elements</span></span>  
 <span data-ttu-id="11344-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="11344-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11344-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11344-119">Parent Elements</span></span>  
  
|<span data-ttu-id="11344-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="11344-120">**Element**</span></span>|<span data-ttu-id="11344-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="11344-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="11344-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="11344-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="11344-123">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="11344-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11344-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11344-124">Remarks</span></span>  
 <span data-ttu-id="11344-125">`add` Element vloží regulární výrazy popisující IP adresy nebo názvy serverů DNS na seznam adres, které obcházejí proxy server.</span><span class="sxs-lookup"><span data-stu-id="11344-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="11344-126">Hodnota `address` atributu by měla být regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="11344-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="11344-127">Při zadávání regulárního výrazu pro tento prvek byste měli použít upozornění.</span><span class="sxs-lookup"><span data-stu-id="11344-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="11344-128">Regulární výraz "[a-z] +\\. contoso\\. com" odpovídá jakémukoli hostiteli v doméně contoso.com, ale také odpovídá jakémukoli hostiteli v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="11344-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="11344-129">Chcete-li spárovat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z] +\\. contoso\\. com $".</span><span class="sxs-lookup"><span data-stu-id="11344-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="11344-130">Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="11344-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="11344-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="11344-131">Configuration Files</span></span>  
 <span data-ttu-id="11344-132">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="11344-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="11344-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="11344-133">Example</span></span>  
 <span data-ttu-id="11344-134">Následující příklad přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="11344-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="11344-135">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresa začíná 192,168.</span><span class="sxs-lookup"><span data-stu-id="11344-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11344-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11344-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="11344-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="11344-137">Network Settings Schema</span></span>](index.md)
