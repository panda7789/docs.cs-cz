---
title: '&lt;Odebrat&gt; Element pro &lt;namedCaches&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6170b59e87948225708c9e697cba1542d756d2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="30968-102">&lt;Odebrat&gt; Element pro &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="30968-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="30968-103">Odebere položku s názvem mezipaměti z `namedCaches` kolekci pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="30968-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="30968-104">\<System.Runtime.Caching – ></span><span class="sxs-lookup"><span data-stu-id="30968-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="30968-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="30968-105">\<memoryCache></span></span>  
<span data-ttu-id="30968-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="30968-106">\<namedCaches></span></span>  
<span data-ttu-id="30968-107">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="30968-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30968-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30968-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="30968-109">Typ</span><span class="sxs-lookup"><span data-stu-id="30968-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30968-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="30968-110">Attributes and Elements</span></span>  
 <span data-ttu-id="30968-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="30968-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30968-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="30968-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="30968-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="30968-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="30968-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="30968-114">Parent Elements</span></span>  
  
|<span data-ttu-id="30968-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="30968-115">Element</span></span>|<span data-ttu-id="30968-116">Popis</span><span class="sxs-lookup"><span data-stu-id="30968-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30968-117">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="30968-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="30968-118">Obsahuje kolekci nastavení konfigurace pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="30968-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30968-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30968-119">Remarks</span></span>  
 <span data-ttu-id="30968-120">`remove` Odebere element `namedCache` položku z kolekce s názvem mezipaměti pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="30968-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30968-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="30968-121">See Also</span></span>  
 [<span data-ttu-id="30968-122">\<namedCaches > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="30968-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
