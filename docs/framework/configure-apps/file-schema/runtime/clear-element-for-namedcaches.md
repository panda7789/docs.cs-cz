---
title: <clear> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: a90970e468359714bbbb858f3f300c26b5757a4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658864"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="860f1-102">\<Clear > element pro \<> namedCaches</span><span class="sxs-lookup"><span data-stu-id="860f1-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="860f1-103">Vymaže všechny `namedCache` položky `namedCaches` v kolekci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="860f1-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="860f1-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="860f1-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="860f1-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="860f1-105">\<memoryCache></span></span>  
<span data-ttu-id="860f1-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="860f1-106">\<namedCaches></span></span>  
<span data-ttu-id="860f1-107">\<add></span><span class="sxs-lookup"><span data-stu-id="860f1-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860f1-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="860f1-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="860f1-109">type</span><span class="sxs-lookup"><span data-stu-id="860f1-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="860f1-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="860f1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="860f1-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="860f1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="860f1-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="860f1-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="860f1-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="860f1-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="860f1-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="860f1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="860f1-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="860f1-115">Element</span></span>|<span data-ttu-id="860f1-116">Popis</span><span class="sxs-lookup"><span data-stu-id="860f1-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="860f1-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="860f1-117">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="860f1-118">Obsahuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="860f1-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="860f1-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="860f1-119">Remarks</span></span>  
 <span data-ttu-id="860f1-120">Element vymaže všechny `namedCache` položky v pojmenované kolekci mezipaměti pro paměťovou mezipaměť. `clear`</span><span class="sxs-lookup"><span data-stu-id="860f1-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="860f1-121">`clear` Element lze použít před `add` použitím elementu k přidání nové pojmenované položky mezipaměti, aby bylo jisté, že v kolekci nejsou žádné další pojmenované mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="860f1-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860f1-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="860f1-122">See also</span></span>

- [<span data-ttu-id="860f1-123">\<namedCaches – element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="860f1-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
