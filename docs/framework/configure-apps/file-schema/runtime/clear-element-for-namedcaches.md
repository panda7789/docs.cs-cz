---
title: '&lt;Vymazat&gt; – Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ea860c185d68a24c31ec24de4a087b9b98fe791f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727804"
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="f215a-102">&lt;Vymazat&gt; – Element pro &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="f215a-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="f215a-103">Vymaže všechny `namedCache` položky `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="f215a-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="f215a-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="f215a-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="f215a-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="f215a-105">\<memoryCache></span></span>  
<span data-ttu-id="f215a-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="f215a-106">\<namedCaches></span></span>  
<span data-ttu-id="f215a-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f215a-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f215a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f215a-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="f215a-109">Typ</span><span class="sxs-lookup"><span data-stu-id="f215a-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f215a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f215a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f215a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f215a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f215a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f215a-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="f215a-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f215a-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="f215a-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f215a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f215a-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="f215a-115">Element</span></span>|<span data-ttu-id="f215a-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f215a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f215a-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="f215a-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="f215a-118">Obsahuje kolekci prvků konfigurace nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instancí.</span><span class="sxs-lookup"><span data-stu-id="f215a-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f215a-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f215a-119">Remarks</span></span>  
 <span data-ttu-id="f215a-120">`clear` Element vymaže všechny `namedCache` položky v kolekci s názvem mezipaměti pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="f215a-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="f215a-121">Můžete použít `clear` prvek před použitím `add` prvek, který chcete přidat novou položku pojmenovanou mezipaměť, aby bylo možné je potřeba mít jistotu, neexistují žádné jiné s názvem mezipaměti v kolekci.</span><span class="sxs-lookup"><span data-stu-id="f215a-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f215a-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f215a-122">See also</span></span>
- [<span data-ttu-id="f215a-123">\<namedcaches – > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="f215a-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
