---
title: <clear> – element pro bypasslist (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 2ad6b16370f600299439d2e810dfefa1b5fa3c06
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087533"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="eaada-102">\<Clear > element pro BypassList (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="eaada-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="eaada-103">Vymaže seznam obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="eaada-103">Clears the proxy bypass list.</span></span>  
  
<span data-ttu-id="eaada-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="eaada-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eaada-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="eaada-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="eaada-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="eaada-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="eaada-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="eaada-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>\
<span data-ttu-id="eaada-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="eaada-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="eaada-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaada-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eaada-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eaada-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eaada-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eaada-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eaada-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="eaada-112">Attributes</span></span>  
 <span data-ttu-id="eaada-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="eaada-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eaada-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eaada-114">Child Elements</span></span>  
 <span data-ttu-id="eaada-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="eaada-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eaada-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eaada-116">Parent Elements</span></span>  
  
|<span data-ttu-id="eaada-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="eaada-117">**Element**</span></span>|<span data-ttu-id="eaada-118">**Popis**</span><span class="sxs-lookup"><span data-stu-id="eaada-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eaada-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="eaada-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="eaada-120">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="eaada-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaada-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eaada-121">Remarks</span></span>  
 <span data-ttu-id="eaada-122">Element `clear` vymaže všechny položky ze seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="eaada-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="eaada-123">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="eaada-123">Configuration Files</span></span>  
 <span data-ttu-id="eaada-124">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="eaada-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaada-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="eaada-125">Example</span></span>  
 <span data-ttu-id="eaada-126">Následující příklad vymaže seznam obcházení a potom přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="eaada-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="eaada-127">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresa začíná 192,168.</span><span class="sxs-lookup"><span data-stu-id="eaada-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="eaada-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaada-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="eaada-129">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="eaada-129">Network Settings Schema</span></span>](index.md)
