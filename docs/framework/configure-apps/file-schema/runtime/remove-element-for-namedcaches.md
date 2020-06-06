---
title: <remove> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252342"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="a2163-102">\<remove> – element pro \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="a2163-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="a2163-103">Odebere pojmenovanou položku mezipaměti z `namedCaches` kolekce pro mezipaměť paměti.</span><span class="sxs-lookup"><span data-stu-id="a2163-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="a2163-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2163-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="a2163-105">Typ</span><span class="sxs-lookup"><span data-stu-id="a2163-105">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2163-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a2163-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a2163-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a2163-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2163-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="a2163-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="a2163-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a2163-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="a2163-110">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a2163-110">Parent Elements</span></span>  
  
|<span data-ttu-id="a2163-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="a2163-111">Element</span></span>|<span data-ttu-id="a2163-112">Description</span><span class="sxs-lookup"><span data-stu-id="a2163-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="a2163-113">Obsahuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="a2163-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2163-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a2163-114">Remarks</span></span>  
 <span data-ttu-id="a2163-115">`remove`Element odebere `namedCache` položku z pojmenované kolekce mezipaměti pro paměťovou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="a2163-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2163-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2163-116">See also</span></span>

- [<span data-ttu-id="a2163-117">\<namedCaches>– Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="a2163-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
