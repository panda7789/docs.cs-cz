---
title: <clear> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252762"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="13f6a-102">\<clear> – element pro \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="13f6a-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="13f6a-103">Vymaže všechny `namedCache` položky v `namedCaches` kolekci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="13f6a-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="13f6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13f6a-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="13f6a-105">Typ</span><span class="sxs-lookup"><span data-stu-id="13f6a-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13f6a-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="13f6a-106">Attributes and Elements</span></span>  
 <span data-ttu-id="13f6a-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="13f6a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13f6a-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="13f6a-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="13f6a-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="13f6a-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="13f6a-110">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="13f6a-110">Parent Elements</span></span>  
  
|<span data-ttu-id="13f6a-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="13f6a-111">Element</span></span>|<span data-ttu-id="13f6a-112">Description</span><span class="sxs-lookup"><span data-stu-id="13f6a-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="13f6a-113">Obsahuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="13f6a-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13f6a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13f6a-114">Remarks</span></span>  
 <span data-ttu-id="13f6a-115">`clear`Element vymaže všechny `namedCache` položky v pojmenované kolekci mezipaměti pro paměťovou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="13f6a-115">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="13f6a-116">Element lze použít `clear` před použitím `add` elementu k přidání nové pojmenované položky mezipaměti, aby bylo jisté, že v kolekci nejsou žádné další pojmenované mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="13f6a-116">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f6a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="13f6a-117">See also</span></span>

- [<span data-ttu-id="13f6a-118">\<namedCaches>– Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="13f6a-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
