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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154943"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="3c728-102">\<bypasslist> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="3c728-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="3c728-103">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="3c728-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="3c728-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c728-104">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c728-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3c728-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3c728-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3c728-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c728-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3c728-107">Attributes</span></span>  
 <span data-ttu-id="3c728-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="3c728-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c728-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3c728-109">Child Elements</span></span>  
  
|<span data-ttu-id="3c728-110">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="3c728-110">**Element**</span></span>|<span data-ttu-id="3c728-111">**Popis**</span><span class="sxs-lookup"><span data-stu-id="3c728-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3c728-112">add</span><span class="sxs-lookup"><span data-stu-id="3c728-112">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="3c728-113">Přidá IP adresu nebo název DNS do seznamu obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="3c728-113">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="3c728-114">jejich</span><span class="sxs-lookup"><span data-stu-id="3c728-114">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="3c728-115">Vymaže seznam obcházení.</span><span class="sxs-lookup"><span data-stu-id="3c728-115">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="3c728-116">odebrány</span><span class="sxs-lookup"><span data-stu-id="3c728-116">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="3c728-117">Odebere IP adresu nebo název DNS ze seznamu obcházení proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="3c728-117">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c728-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3c728-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3c728-119">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="3c728-119">**Element**</span></span>|<span data-ttu-id="3c728-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="3c728-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3c728-121">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="3c728-121">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="3c728-122">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="3c728-122">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c728-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c728-123">Remarks</span></span>  
 <span data-ttu-id="3c728-124">Seznam pro obejití obsahuje regulární výrazy, které popisují identifikátory URI, které <xref:System.Net.WebRequest> instance přistupuje přímo místo přes proxy server.</span><span class="sxs-lookup"><span data-stu-id="3c728-124">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="3c728-125">Při zadávání regulárního výrazu pro tento prvek byste měli použít upozornění.</span><span class="sxs-lookup"><span data-stu-id="3c728-125">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="3c728-126">Regulární výraz "[a-z] + \\ . contoso \\ . com" odpovídá jakémukoli hostiteli v doméně contoso.com, ale také odpovídá jakémukoli hostiteli v doméně contoso.com.cpandl.com.</span><span class="sxs-lookup"><span data-stu-id="3c728-126">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="3c728-127">Chcete-li spárovat pouze hostitele v doméně contoso.com, použijte kotvu ("$"): "[a-z] + \\ . contoso \\ . com $".</span><span class="sxs-lookup"><span data-stu-id="3c728-127">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="3c728-128">Další informace o regulárních výrazech naleznete v tématu. [.NET Framework regulární výrazy](../../../../standard/base-types/regular-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3c728-128">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3c728-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="3c728-129">Configuration Files</span></span>  
 <span data-ttu-id="3c728-130">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="3c728-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c728-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="3c728-131">Example</span></span>  
 <span data-ttu-id="3c728-132">Následující příklad přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="3c728-132">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="3c728-133">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresy začínají na 192,168.</span><span class="sxs-lookup"><span data-stu-id="3c728-133">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3c728-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c728-134">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="3c728-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="3c728-135">Network Settings Schema</span></span>](index.md)
