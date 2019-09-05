---
title: <remove> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252342"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="b3c15-102">\<Odebrat element > pro \<> namedCaches</span><span class="sxs-lookup"><span data-stu-id="b3c15-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="b3c15-103">Odebere pojmenovanou položku mezipaměti z `namedCaches` kolekce pro mezipaměť paměti.</span><span class="sxs-lookup"><span data-stu-id="b3c15-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="b3c15-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b3c15-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b3c15-105">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b3c15-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="b3c15-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b3c15-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="b3c15-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b3c15-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="b3c15-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="b3c15-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c15-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3c15-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="b3c15-110">type</span><span class="sxs-lookup"><span data-stu-id="b3c15-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3c15-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b3c15-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b3c15-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b3c15-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3c15-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="b3c15-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="b3c15-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b3c15-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="b3c15-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b3c15-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b3c15-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="b3c15-116">Element</span></span>|<span data-ttu-id="b3c15-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b3c15-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3c15-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="b3c15-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="b3c15-119">Obsahuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="b3c15-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3c15-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3c15-120">Remarks</span></span>  
 <span data-ttu-id="b3c15-121">`remove` Element`namedCache` odebere položku z pojmenované kolekce mezipaměti pro paměťovou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="b3c15-121">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c15-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3c15-122">See also</span></span>

- [<span data-ttu-id="b3c15-123">\<namedCaches – element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="b3c15-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
