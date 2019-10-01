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
ms.openlocfilehash: 1dda43be8c0e0c94bdf7b57b67aa4d403b547f97
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699545"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="0f4e2-102">@no__t – element > 0bypasslist (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="0f4e2-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="0f4e2-103">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
[<span data-ttu-id="0f4e2-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="0f4e2-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0f4e2-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0f4e2-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="0f4e2-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0f4e2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="0f4e2-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<bypasslist >**</span><span class="sxs-lookup"><span data-stu-id="0f4e2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f4e2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f4e2-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f4e2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0f4e2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0f4e2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f4e2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="0f4e2-111">Attributes</span></span>  
 <span data-ttu-id="0f4e2-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="0f4e2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0f4e2-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0f4e2-113">Child Elements</span></span>  
  
|<span data-ttu-id="0f4e2-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="0f4e2-114">**Element**</span></span>|<span data-ttu-id="0f4e2-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0f4e2-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0f4e2-116">add</span><span class="sxs-lookup"><span data-stu-id="0f4e2-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="0f4e2-117">Přidá IP adresu nebo název DNS do seznamu obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="0f4e2-118">jejich</span><span class="sxs-lookup"><span data-stu-id="0f4e2-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="0f4e2-119">Vymaže seznam obcházení.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="0f4e2-120">remove</span><span class="sxs-lookup"><span data-stu-id="0f4e2-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="0f4e2-121">Odebere IP adresu nebo název DNS ze seznamu obcházení proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0f4e2-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0f4e2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0f4e2-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="0f4e2-123">**Element**</span></span>|<span data-ttu-id="0f4e2-124">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0f4e2-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0f4e2-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="0f4e2-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="0f4e2-126">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="0f4e2-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f4e2-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f4e2-127">Remarks</span></span>  
 <span data-ttu-id="0f4e2-128">Seznam pro obejití obsahuje regulární výrazy, které popisují identifikátory URI, které <xref:System.Net.WebRequest> instancí přímo, nikoli prostřednictvím proxy server.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="0f4e2-129">Při zadávání regulárního výrazu pro tento prvek byste měli použít upozornění.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="0f4e2-130">Regulární výraz "[a-z] + @no__t -0.contoso\\.com" odpovídá jakémukoli hostiteli v doméně contoso.com, ale také odpovídá jakémukoli hostiteli v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="0f4e2-131">Chcete-li spárovat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z] + @no__t -0.contoso\\.com $".</span><span class="sxs-lookup"><span data-stu-id="0f4e2-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="0f4e2-132">Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0f4e2-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0f4e2-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="0f4e2-133">Configuration Files</span></span>  
 <span data-ttu-id="0f4e2-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="0f4e2-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f4e2-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f4e2-135">Example</span></span>  
 <span data-ttu-id="0f4e2-136">Následující příklad přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="0f4e2-137">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresy začínají na 192,168.</span><span class="sxs-lookup"><span data-stu-id="0f4e2-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f4e2-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f4e2-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="0f4e2-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="0f4e2-139">Network Settings Schema</span></span>](index.md)
