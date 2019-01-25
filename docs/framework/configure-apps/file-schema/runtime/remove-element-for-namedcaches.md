---
title: '&lt;Odebrat&gt; – Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7e183a624b95e207d34697c906cc3f278c967ae9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499769"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="528e6-102">&lt;Odebrat&gt; – Element pro &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="528e6-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="528e6-103">Odebere položku pojmenovanou mezipaměť z `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="528e6-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="528e6-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="528e6-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="528e6-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="528e6-105">\<memoryCache></span></span>  
<span data-ttu-id="528e6-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="528e6-106">\<namedCaches></span></span>  
<span data-ttu-id="528e6-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="528e6-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528e6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="528e6-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="528e6-109">Typ</span><span class="sxs-lookup"><span data-stu-id="528e6-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="528e6-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="528e6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="528e6-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="528e6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="528e6-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="528e6-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="528e6-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="528e6-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="528e6-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="528e6-114">Parent Elements</span></span>  
  
|<span data-ttu-id="528e6-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="528e6-115">Element</span></span>|<span data-ttu-id="528e6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="528e6-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="528e6-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="528e6-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="528e6-118">Obsahuje kolekci prvků konfigurace nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instancí.</span><span class="sxs-lookup"><span data-stu-id="528e6-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="528e6-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="528e6-119">Remarks</span></span>  
 <span data-ttu-id="528e6-120">`remove` Odebere element `namedCache` položku z kolekce s názvem mezipaměti pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="528e6-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528e6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="528e6-121">See also</span></span>
- [<span data-ttu-id="528e6-122">\<namedcaches – > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="528e6-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
