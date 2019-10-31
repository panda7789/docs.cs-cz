---
title: COR_IL_MAP – struktura
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: c37f039d9636854c464e7981693c573bd60deab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132346"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="65415-102">COR_IL_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="65415-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="65415-103">Určuje změny relativního posunu funkce.</span><span class="sxs-lookup"><span data-stu-id="65415-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65415-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65415-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="65415-105">Členové</span><span class="sxs-lookup"><span data-stu-id="65415-105">Members</span></span>  
  
|<span data-ttu-id="65415-106">Člen</span><span class="sxs-lookup"><span data-stu-id="65415-106">Member</span></span>|<span data-ttu-id="65415-107">Popis</span><span class="sxs-lookup"><span data-stu-id="65415-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="65415-108">Starý posun jazyka MSIL (Microsoft Intermediate Language) vzhledem k začátku funkce.</span><span class="sxs-lookup"><span data-stu-id="65415-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="65415-109">Nový posun MSIL vzhledem k začátku funkce.</span><span class="sxs-lookup"><span data-stu-id="65415-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="65415-110">`true`, pokud je známé správné mapování; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="65415-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65415-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65415-111">Remarks</span></span>  
 <span data-ttu-id="65415-112">Formát mapy je následující: ladicí program předpokládá, že `oldOffset` odkazuje na posun MSIL v rámci původního neupraveného kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="65415-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="65415-113">Parametr `newOffset` odkazuje na odpovídající posun MSIL v rámci nového, instrumentované kódu.</span><span class="sxs-lookup"><span data-stu-id="65415-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="65415-114">Aby krokování fungovalo správně, měli byste splnit následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="65415-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="65415-115">Mapa by se měla seřadit ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="65415-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="65415-116">Instrumentované kódy MSIL by se neměly přeřadit.</span><span class="sxs-lookup"><span data-stu-id="65415-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="65415-117">Původní kód MSIL by neměl být odebrán.</span><span class="sxs-lookup"><span data-stu-id="65415-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="65415-118">Mapa by měla obsahovat položky pro mapování všech bodů sekvence ze souboru databáze programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="65415-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="65415-119">Mapa neinterpoluje chybějící položky.</span><span class="sxs-lookup"><span data-stu-id="65415-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="65415-120">Následující příklad ukazuje mapu a její výsledky.</span><span class="sxs-lookup"><span data-stu-id="65415-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="65415-121">Mapy</span><span class="sxs-lookup"><span data-stu-id="65415-121">Map:</span></span>  
  
- <span data-ttu-id="65415-122">0 staré odsazení, 0 nového posunu</span><span class="sxs-lookup"><span data-stu-id="65415-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="65415-123">5 Old posun, 10 nových posunů</span><span class="sxs-lookup"><span data-stu-id="65415-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="65415-124">9 staré posunutí, 20 nových posunů</span><span class="sxs-lookup"><span data-stu-id="65415-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="65415-125">Důsledk</span><span class="sxs-lookup"><span data-stu-id="65415-125">Results:</span></span>  
  
- <span data-ttu-id="65415-126">Starý posun 0, 1, 2, 3 nebo 4 se namapuje na nový posun 0.</span><span class="sxs-lookup"><span data-stu-id="65415-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="65415-127">Starý posun z 5, 6, 7 nebo 8 se namapuje na nový posun 10.</span><span class="sxs-lookup"><span data-stu-id="65415-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="65415-128">Původní posun 9 nebo vyšší se namapuje na nový posun 20.</span><span class="sxs-lookup"><span data-stu-id="65415-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="65415-129">Nové odsazení 0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 bude namapováno na starý posun 0.</span><span class="sxs-lookup"><span data-stu-id="65415-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="65415-130">Nové posuny 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 budou namapovány na starý posun 5.</span><span class="sxs-lookup"><span data-stu-id="65415-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="65415-131">Nový posun o hodnotě 20 nebo vyšší bude mapován na starý posun 9.</span><span class="sxs-lookup"><span data-stu-id="65415-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65415-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65415-132">Requirements</span></span>  
 <span data-ttu-id="65415-133">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65415-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65415-134">**Hlavička:** CorDebug. idl, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="65415-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="65415-135">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="65415-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65415-136">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65415-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65415-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65415-137">See also</span></span>

- [<span data-ttu-id="65415-138">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="65415-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="65415-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="65415-139">Debugging</span></span>](index.md)
