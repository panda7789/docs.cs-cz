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
ms.openlocfilehash: 10d2a025096579c6bed64f82cc955deb0542717c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664207"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="81e29-102">\<BypassList – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="81e29-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="81e29-103">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="81e29-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="81e29-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="81e29-104">\<configuration></span></span>  
<span data-ttu-id="81e29-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="81e29-105">\<system.net></span></span>  
<span data-ttu-id="81e29-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="81e29-106">\<defaultProxy></span></span>  
<span data-ttu-id="81e29-107">\<BypassList ></span><span class="sxs-lookup"><span data-stu-id="81e29-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e29-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81e29-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81e29-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="81e29-109">Attributes and Elements</span></span>  
 <span data-ttu-id="81e29-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="81e29-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81e29-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="81e29-111">Attributes</span></span>  
 <span data-ttu-id="81e29-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="81e29-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="81e29-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="81e29-113">Child Elements</span></span>  
  
|<span data-ttu-id="81e29-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="81e29-114">**Element**</span></span>|<span data-ttu-id="81e29-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="81e29-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="81e29-116">add</span><span class="sxs-lookup"><span data-stu-id="81e29-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="81e29-117">Přidá IP adresu nebo název DNS do seznamu obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="81e29-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="81e29-118">jejich</span><span class="sxs-lookup"><span data-stu-id="81e29-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="81e29-119">Vymaže seznam obcházení.</span><span class="sxs-lookup"><span data-stu-id="81e29-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="81e29-120">remove</span><span class="sxs-lookup"><span data-stu-id="81e29-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="81e29-121">Odebere IP adresu nebo název DNS ze seznamu obcházení proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="81e29-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81e29-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="81e29-122">Parent Elements</span></span>  
  
|<span data-ttu-id="81e29-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="81e29-123">**Element**</span></span>|<span data-ttu-id="81e29-124">**Popis**</span><span class="sxs-lookup"><span data-stu-id="81e29-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="81e29-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="81e29-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="81e29-126">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="81e29-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81e29-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81e29-127">Remarks</span></span>  
 <span data-ttu-id="81e29-128">Seznam pro obejití obsahuje regulární výrazy, které popisují identifikátory <xref:System.Net.WebRequest> URI, které instance přistupuje přímo místo přes proxy server.</span><span class="sxs-lookup"><span data-stu-id="81e29-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="81e29-129">Při zadávání regulárního výrazu pro tento prvek byste měli použít upozornění.</span><span class="sxs-lookup"><span data-stu-id="81e29-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="81e29-130">Regulární výraz "[a-z] +\\. contoso\\. com" odpovídá jakémukoli hostiteli v doméně contoso.com, ale také odpovídá jakémukoli hostiteli v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="81e29-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="81e29-131">Chcete-li spárovat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z] +\\. contoso\\. com $".</span><span class="sxs-lookup"><span data-stu-id="81e29-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="81e29-132">Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../../docs/standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="81e29-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="81e29-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="81e29-133">Configuration Files</span></span>  
 <span data-ttu-id="81e29-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="81e29-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81e29-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="81e29-135">Example</span></span>  
 <span data-ttu-id="81e29-136">Následující příklad přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="81e29-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="81e29-137">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresy začínají na 192,168.</span><span class="sxs-lookup"><span data-stu-id="81e29-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81e29-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81e29-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="81e29-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="81e29-139">Network Settings Schema</span></span>](index.md)
