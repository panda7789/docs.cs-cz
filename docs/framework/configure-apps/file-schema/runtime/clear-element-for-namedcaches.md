---
title: <clear> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: eb0a50919e163a795abc70d132bd45f1d05192ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146858"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="12e27-102">\<Vymazat > – Element pro \<namedcaches – ></span><span class="sxs-lookup"><span data-stu-id="12e27-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="12e27-103">Vymaže všechny `namedCache` položky `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="12e27-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="12e27-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="12e27-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="12e27-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="12e27-105">\<memoryCache></span></span>  
<span data-ttu-id="12e27-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="12e27-106">\<namedCaches></span></span>  
<span data-ttu-id="12e27-107">\<add></span><span class="sxs-lookup"><span data-stu-id="12e27-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e27-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12e27-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="12e27-109">Type</span><span class="sxs-lookup"><span data-stu-id="12e27-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12e27-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="12e27-110">Attributes and Elements</span></span>  
 <span data-ttu-id="12e27-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="12e27-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12e27-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="12e27-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="12e27-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="12e27-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="12e27-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="12e27-114">Parent Elements</span></span>  
  
|<span data-ttu-id="12e27-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="12e27-115">Element</span></span>|<span data-ttu-id="12e27-116">Popis</span><span class="sxs-lookup"><span data-stu-id="12e27-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12e27-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="12e27-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="12e27-118">Obsahuje kolekci prvků konfigurace nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instancí.</span><span class="sxs-lookup"><span data-stu-id="12e27-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12e27-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12e27-119">Remarks</span></span>  
 <span data-ttu-id="12e27-120">`clear` Element vymaže všechny `namedCache` položky v kolekci s názvem mezipaměti pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="12e27-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="12e27-121">Můžete použít `clear` prvek před použitím `add` prvek, který chcete přidat novou položku pojmenovanou mezipaměť, aby bylo možné je potřeba mít jistotu, neexistují žádné jiné s názvem mezipaměti v kolekci.</span><span class="sxs-lookup"><span data-stu-id="12e27-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e27-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12e27-122">See also</span></span>

- [<span data-ttu-id="12e27-123">\<namedcaches – > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="12e27-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
