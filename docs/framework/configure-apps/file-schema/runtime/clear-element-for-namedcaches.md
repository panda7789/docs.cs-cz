---
title: '&lt;Vymazat&gt; Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cdd6e4a4849a031dc6bcad909509498406fcb129
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745510"
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="f3dda-102">&lt;Vymazat&gt; Element pro &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="f3dda-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="f3dda-103">Vymaže všechny `namedCache` položek v `namedCaches` kolekci pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="f3dda-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="f3dda-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="f3dda-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="f3dda-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="f3dda-105">\<memoryCache></span></span>  
<span data-ttu-id="f3dda-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="f3dda-106">\<namedCaches></span></span>  
<span data-ttu-id="f3dda-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f3dda-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3dda-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3dda-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="f3dda-109">Typ</span><span class="sxs-lookup"><span data-stu-id="f3dda-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3dda-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3dda-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f3dda-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3dda-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3dda-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3dda-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="f3dda-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3dda-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="f3dda-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3dda-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f3dda-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3dda-115">Element</span></span>|<span data-ttu-id="f3dda-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f3dda-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3dda-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="f3dda-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="f3dda-118">Obsahuje kolekci nastavení konfigurace pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="f3dda-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3dda-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3dda-119">Remarks</span></span>  
 <span data-ttu-id="f3dda-120">`clear` Element vymaže všechny `namedCache` položky v kolekci s názvem mezipaměti pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="f3dda-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="f3dda-121">Můžete použít `clear` element před použitím `add` elementu, který chcete přidat novou položku s názvem mezipaměti Chcete-li být jistý, neexistují žádné další s názvem mezipaměti v kolekci.</span><span class="sxs-lookup"><span data-stu-id="f3dda-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3dda-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3dda-122">See Also</span></span>  
 [<span data-ttu-id="f3dda-123">\<namedCaches > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="f3dda-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
