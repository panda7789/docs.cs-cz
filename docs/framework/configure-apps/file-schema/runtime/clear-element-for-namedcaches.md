---
title: <clear> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252762"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="61fe4-102">\<Clear > element pro \<> namedCaches</span><span class="sxs-lookup"><span data-stu-id="61fe4-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="61fe4-103">Vymaže všechny `namedCache` položky `namedCaches` v kolekci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="61fe4-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="61fe4-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="61fe4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="61fe4-105">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="61fe4-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="61fe4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="61fe4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="61fe4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="61fe4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="61fe4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Vymazat >**</span><span class="sxs-lookup"><span data-stu-id="61fe4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61fe4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61fe4-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="61fe4-110">type</span><span class="sxs-lookup"><span data-stu-id="61fe4-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61fe4-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="61fe4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="61fe4-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="61fe4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61fe4-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="61fe4-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="61fe4-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="61fe4-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="61fe4-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="61fe4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="61fe4-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="61fe4-116">Element</span></span>|<span data-ttu-id="61fe4-117">Popis</span><span class="sxs-lookup"><span data-stu-id="61fe4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61fe4-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="61fe4-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="61fe4-119">Obsahuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="61fe4-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61fe4-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61fe4-120">Remarks</span></span>  
 <span data-ttu-id="61fe4-121">Element vymaže všechny `namedCache` položky v pojmenované kolekci mezipaměti pro paměťovou mezipaměť. `clear`</span><span class="sxs-lookup"><span data-stu-id="61fe4-121">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="61fe4-122">`clear` Element lze použít před `add` použitím elementu k přidání nové pojmenované položky mezipaměti, aby bylo jisté, že v kolekci nejsou žádné další pojmenované mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61fe4-122">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61fe4-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61fe4-123">See also</span></span>

- [<span data-ttu-id="61fe4-124">\<namedCaches – element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="61fe4-124">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
