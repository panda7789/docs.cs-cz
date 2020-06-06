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
ms.openlocfilehash: c25477c2c99be66b34b07e1f7e50115bfa8d14e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154930"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="975ac-102">\<clear> – element pro bypasslist (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="975ac-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="975ac-103">Vymaže seznam obcházení proxy serverů.</span><span class="sxs-lookup"><span data-stu-id="975ac-103">Clears the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="975ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="975ac-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="975ac-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="975ac-105">Attributes and Elements</span></span>  
 <span data-ttu-id="975ac-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="975ac-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="975ac-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="975ac-107">Attributes</span></span>  
 <span data-ttu-id="975ac-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="975ac-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="975ac-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="975ac-109">Child Elements</span></span>  
 <span data-ttu-id="975ac-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="975ac-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="975ac-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="975ac-111">Parent Elements</span></span>  
  
|<span data-ttu-id="975ac-112">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="975ac-112">**Element**</span></span>|<span data-ttu-id="975ac-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="975ac-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="975ac-114">bypasslist</span><span class="sxs-lookup"><span data-stu-id="975ac-114">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="975ac-115">Poskytuje sadu regulárních výrazů, které popisují adresy, které nepoužívají proxy server.</span><span class="sxs-lookup"><span data-stu-id="975ac-115">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="975ac-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="975ac-116">Remarks</span></span>  
 <span data-ttu-id="975ac-117">`clear`Prvek vymaže všechny položky ze seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="975ac-117">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="975ac-118">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="975ac-118">Configuration Files</span></span>  
 <span data-ttu-id="975ac-119">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="975ac-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="975ac-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="975ac-120">Example</span></span>  
 <span data-ttu-id="975ac-121">Následující příklad vymaže seznam obcházení a potom přidá dvě adresy do seznamu pro obejití.</span><span class="sxs-lookup"><span data-stu-id="975ac-121">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="975ac-122">První obchází proxy server pro všechny servery v doméně contoso.com; Druhá obchází proxy server pro všechny servery, jejichž IP adresa začíná 192,168.</span><span class="sxs-lookup"><span data-stu-id="975ac-122">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="975ac-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="975ac-123">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="975ac-124">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="975ac-124">Network Settings Schema</span></span>](index.md)
