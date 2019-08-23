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
ms.openlocfilehash: da234402c6ec7e2c1f85e4bd674517b1147f0d18
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927480"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="17889-102">\<Přidat > element pro BypassList (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="17889-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="17889-103">Přidá IP adresu nebo název DNS do seznamu obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="17889-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="17889-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="17889-104">\<configuration></span></span>  
<span data-ttu-id="17889-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="17889-105">\<system.net></span></span>  
<span data-ttu-id="17889-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="17889-106">\<defaultProxy></span></span>  
<span data-ttu-id="17889-107">\<BypassList ></span><span class="sxs-lookup"><span data-stu-id="17889-107">\<bypasslist></span></span>  
<span data-ttu-id="17889-108">\<add></span><span class="sxs-lookup"><span data-stu-id="17889-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17889-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17889-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17889-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="17889-110">Attributes and Elements</span></span>  
 <span data-ttu-id="17889-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="17889-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17889-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="17889-112">Attributes</span></span>  
  
|<span data-ttu-id="17889-113">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="17889-113">**Attribute**</span></span>|<span data-ttu-id="17889-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="17889-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="17889-115">**address**</span><span class="sxs-lookup"><span data-stu-id="17889-115">**address**</span></span>|<span data-ttu-id="17889-116">Regulární výraz popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="17889-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17889-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="17889-117">Child Elements</span></span>  
 <span data-ttu-id="17889-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="17889-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17889-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="17889-119">Parent Elements</span></span>  
  
|<span data-ttu-id="17889-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="17889-120">**Element**</span></span>|<span data-ttu-id="17889-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="17889-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="17889-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="17889-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="17889-123">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="17889-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17889-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17889-124">Remarks</span></span>  
 <span data-ttu-id="17889-125">`add` Element vloží regulární výrazy popisující IP adresy nebo názvy serverů DNS na seznam adres, které obcházejí proxy server.</span><span class="sxs-lookup"><span data-stu-id="17889-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="17889-126">Hodnota `address` atributu by měla být regulární výraz, který popisuje sadu IP adres nebo názvů hostitelů.</span><span class="sxs-lookup"><span data-stu-id="17889-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="17889-127">Při zadávání regulárního výrazu pro tento prvek byste měli použít upozornění.</span><span class="sxs-lookup"><span data-stu-id="17889-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="17889-128">Regulární výraz "[a-z] +\\. contoso\\. com" odpovídá jakémukoli hostiteli v doméně contoso.com, ale také odpovídá jakémukoli hostiteli v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="17889-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="17889-129">Chcete-li spárovat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z] +\\. contoso\\. com $".</span><span class="sxs-lookup"><span data-stu-id="17889-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="17889-130">Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="17889-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="17889-131">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="17889-131">Configuration Files</span></span>  
 <span data-ttu-id="17889-132">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="17889-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17889-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="17889-133">Example</span></span>  
 <span data-ttu-id="17889-134">Následující příklad přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="17889-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="17889-135">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresa začíná 192,168.</span><span class="sxs-lookup"><span data-stu-id="17889-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17889-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17889-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="17889-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="17889-137">Network Settings Schema</span></span>](index.md)
