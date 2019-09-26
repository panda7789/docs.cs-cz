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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ae4c5743b01c4a9087323678d315473631cb32f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274041"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="f29ee-102">COR_IL_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="f29ee-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="f29ee-103">Určuje změny relativního posunu funkce.</span><span class="sxs-lookup"><span data-stu-id="f29ee-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f29ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f29ee-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="f29ee-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f29ee-105">Members</span></span>  
  
|<span data-ttu-id="f29ee-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f29ee-106">Member</span></span>|<span data-ttu-id="f29ee-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f29ee-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="f29ee-108">Starý posun jazyka MSIL (Microsoft Intermediate Language) vzhledem k začátku funkce.</span><span class="sxs-lookup"><span data-stu-id="f29ee-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="f29ee-109">Nový posun MSIL vzhledem k začátku funkce.</span><span class="sxs-lookup"><span data-stu-id="f29ee-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="f29ee-110">`true`je-li mapování známo, že je přesné; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="f29ee-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f29ee-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f29ee-111">Remarks</span></span>  
 <span data-ttu-id="f29ee-112">Formát mapy je následující: Ladicí program bude předpokládat, `oldOffset` že odkazuje na posun MSIL v rámci původního nezměněného kódu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="f29ee-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="f29ee-113">`newOffset` Parametr odkazuje na odpovídající posun MSIL v rámci nového, instrumentované kódu.</span><span class="sxs-lookup"><span data-stu-id="f29ee-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="f29ee-114">Aby krokování fungovalo správně, měli byste splnit následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="f29ee-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="f29ee-115">Mapa by se měla seřadit ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f29ee-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="f29ee-116">Instrumentované kódy MSIL by se neměly přeřadit.</span><span class="sxs-lookup"><span data-stu-id="f29ee-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="f29ee-117">Původní kód MSIL by neměl být odebrán.</span><span class="sxs-lookup"><span data-stu-id="f29ee-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="f29ee-118">Mapa by měla obsahovat položky pro mapování všech bodů sekvence ze souboru databáze programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="f29ee-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="f29ee-119">Mapa neinterpoluje chybějící položky.</span><span class="sxs-lookup"><span data-stu-id="f29ee-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="f29ee-120">Následující příklad ukazuje mapu a její výsledky.</span><span class="sxs-lookup"><span data-stu-id="f29ee-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="f29ee-121">Mapy</span><span class="sxs-lookup"><span data-stu-id="f29ee-121">Map:</span></span>  
  
- <span data-ttu-id="f29ee-122">0 staré odsazení, 0 nového posunu</span><span class="sxs-lookup"><span data-stu-id="f29ee-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="f29ee-123">5 Old posun, 10 nových posunů</span><span class="sxs-lookup"><span data-stu-id="f29ee-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="f29ee-124">9 staré posunutí, 20 nových posunů</span><span class="sxs-lookup"><span data-stu-id="f29ee-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="f29ee-125">Důsledk</span><span class="sxs-lookup"><span data-stu-id="f29ee-125">Results:</span></span>  
  
- <span data-ttu-id="f29ee-126">Starý posun 0, 1, 2, 3 nebo 4 se namapuje na nový posun 0.</span><span class="sxs-lookup"><span data-stu-id="f29ee-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="f29ee-127">Starý posun z 5, 6, 7 nebo 8 se namapuje na nový posun 10.</span><span class="sxs-lookup"><span data-stu-id="f29ee-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="f29ee-128">Původní posun 9 nebo vyšší se namapuje na nový posun 20.</span><span class="sxs-lookup"><span data-stu-id="f29ee-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="f29ee-129">Nové odsazení 0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 bude namapováno na starý posun 0.</span><span class="sxs-lookup"><span data-stu-id="f29ee-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="f29ee-130">Nové posuny 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 budou namapovány na starý posun 5.</span><span class="sxs-lookup"><span data-stu-id="f29ee-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="f29ee-131">Nový posun o hodnotě 20 nebo vyšší bude mapován na starý posun 9.</span><span class="sxs-lookup"><span data-stu-id="f29ee-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f29ee-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f29ee-132">Requirements</span></span>  
 <span data-ttu-id="f29ee-133">**Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f29ee-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f29ee-134">**Hlaviček** CorDebug. idl, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="f29ee-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="f29ee-135">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f29ee-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f29ee-136">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f29ee-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f29ee-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f29ee-137">See also</span></span>

- [<span data-ttu-id="f29ee-138">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="f29ee-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="f29ee-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="f29ee-139">Debugging</span></span>](index.md)
