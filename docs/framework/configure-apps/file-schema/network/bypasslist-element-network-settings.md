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
ms.openlocfilehash: 7a6c1282c9ca8381d2dbb21ffdc82f95732c42b3
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087527"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="8885d-102">\<element > BypassList (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8885d-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="8885d-103">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="8885d-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="8885d-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8885d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8885d-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8885d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="8885d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8885d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="8885d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bypasslist >**</span><span class="sxs-lookup"><span data-stu-id="8885d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8885d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8885d-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8885d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8885d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8885d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8885d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8885d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8885d-111">Attributes</span></span>  
 <span data-ttu-id="8885d-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="8885d-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8885d-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8885d-113">Child Elements</span></span>  
  
|<span data-ttu-id="8885d-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="8885d-114">**Element**</span></span>|<span data-ttu-id="8885d-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8885d-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8885d-116">add</span><span class="sxs-lookup"><span data-stu-id="8885d-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="8885d-117">Přidá IP adresu nebo název DNS do seznamu obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="8885d-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="8885d-118">jejich</span><span class="sxs-lookup"><span data-stu-id="8885d-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="8885d-119">Vymaže seznam obcházení.</span><span class="sxs-lookup"><span data-stu-id="8885d-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="8885d-120">remove</span><span class="sxs-lookup"><span data-stu-id="8885d-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="8885d-121">Odebere IP adresu nebo název DNS ze seznamu obcházení proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="8885d-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8885d-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8885d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8885d-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="8885d-123">**Element**</span></span>|<span data-ttu-id="8885d-124">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8885d-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8885d-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="8885d-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="8885d-126">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="8885d-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8885d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8885d-127">Remarks</span></span>  
 <span data-ttu-id="8885d-128">Seznam pro obejití obsahuje regulární výrazy, které popisují identifikátory URI, které <xref:System.Net.WebRequest> instancích přímo místo přes proxy server.</span><span class="sxs-lookup"><span data-stu-id="8885d-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="8885d-129">Při zadávání regulárního výrazu pro tento prvek byste měli použít upozornění.</span><span class="sxs-lookup"><span data-stu-id="8885d-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="8885d-130">Regulární výraz "[a-z] +\\. contoso\\. com" odpovídá jakémukoli hostiteli v doméně contoso.com, ale také odpovídá jakémukoli hostiteli v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="8885d-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="8885d-131">Chcete-li spárovat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z] +\\. contoso\\. com $".</span><span class="sxs-lookup"><span data-stu-id="8885d-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="8885d-132">Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8885d-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8885d-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="8885d-133">Configuration Files</span></span>  
 <span data-ttu-id="8885d-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8885d-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8885d-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="8885d-135">Example</span></span>  
 <span data-ttu-id="8885d-136">Následující příklad přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="8885d-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="8885d-137">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresy začínají na 192,168.</span><span class="sxs-lookup"><span data-stu-id="8885d-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8885d-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8885d-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="8885d-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8885d-139">Network Settings Schema</span></span>](index.md)
