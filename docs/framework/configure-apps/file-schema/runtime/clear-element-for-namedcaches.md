---
title: <clear> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: e563f8f27538e70ba90465fc28d300754509f7a4
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423311"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="398c7-102">\<Vymazat > – Element pro \<namedcaches – ></span><span class="sxs-lookup"><span data-stu-id="398c7-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="398c7-103">Vymaže všechny `namedCache` položky `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="398c7-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="398c7-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="398c7-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="398c7-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="398c7-105">\<memoryCache></span></span>  
<span data-ttu-id="398c7-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="398c7-106">\<namedCaches></span></span>  
<span data-ttu-id="398c7-107">\<add></span><span class="sxs-lookup"><span data-stu-id="398c7-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="398c7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="398c7-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="398c7-109">type</span><span class="sxs-lookup"><span data-stu-id="398c7-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="398c7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="398c7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="398c7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="398c7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="398c7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="398c7-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="398c7-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="398c7-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="398c7-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="398c7-114">Parent Elements</span></span>  
  
|<span data-ttu-id="398c7-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="398c7-115">Element</span></span>|<span data-ttu-id="398c7-116">Popis</span><span class="sxs-lookup"><span data-stu-id="398c7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="398c7-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="398c7-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="398c7-118">Obsahuje kolekci prvků konfigurace nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instancí.</span><span class="sxs-lookup"><span data-stu-id="398c7-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="398c7-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="398c7-119">Remarks</span></span>  
 <span data-ttu-id="398c7-120">`clear` Element vymaže všechny `namedCache` položky v kolekci s názvem mezipaměti pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="398c7-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="398c7-121">Můžete použít `clear` prvek před použitím `add` prvek, který chcete přidat novou položku pojmenovanou mezipaměť, aby bylo možné je potřeba mít jistotu, neexistují žádné jiné s názvem mezipaměti v kolekci.</span><span class="sxs-lookup"><span data-stu-id="398c7-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="398c7-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="398c7-122">See also</span></span>

- [<span data-ttu-id="398c7-123">\<namedcaches – > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="398c7-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
