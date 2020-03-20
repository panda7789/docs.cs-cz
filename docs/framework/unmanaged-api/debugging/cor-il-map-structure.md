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
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179295"
---
# <a name="cor_il_map-structure"></a><span data-ttu-id="5f791-102">COR_IL_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="5f791-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="5f791-103">Určuje změny v relativním odsazení funkce.</span><span class="sxs-lookup"><span data-stu-id="5f791-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f791-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f791-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="5f791-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5f791-105">Members</span></span>  
  
|<span data-ttu-id="5f791-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5f791-106">Member</span></span>|<span data-ttu-id="5f791-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5f791-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="5f791-108">Starý microsoft zprostředkující jazyk (MSIL) posun vzhledem k začátku funkce.</span><span class="sxs-lookup"><span data-stu-id="5f791-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="5f791-109">Nový posun MSIL vzhledem k začátku funkce.</span><span class="sxs-lookup"><span data-stu-id="5f791-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="5f791-110">`true`je-li známo, že mapování je přesné; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="5f791-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f791-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5f791-111">Remarks</span></span>  
 <span data-ttu-id="5f791-112">Formát mapy je následující: Ladicí program bude `oldOffset` předpokládat, že odkazuje na posun MSIL v rámci původního, neupraveného kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="5f791-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="5f791-113">Parametr `newOffset` odkazuje na odpovídající posun MSIL v rámci nového instrumentovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5f791-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="5f791-114">Pro krokování správně fungovat, by měly být splněny následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="5f791-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="5f791-115">Mapa by měla být seřazena vzestupně.</span><span class="sxs-lookup"><span data-stu-id="5f791-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="5f791-116">Instrumentovaný kód MSIL by neměl být přeřazen.</span><span class="sxs-lookup"><span data-stu-id="5f791-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="5f791-117">Původní kód MSIL by neměl být odebrán.</span><span class="sxs-lookup"><span data-stu-id="5f791-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="5f791-118">Mapa by měla obsahovat položky k mapování všech sekvenčních bodů ze souboru databáze programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="5f791-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="5f791-119">Mapa neinterpoluje chybějící položky.</span><span class="sxs-lookup"><span data-stu-id="5f791-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="5f791-120">Následující příklad ukazuje mapu a její výsledky.</span><span class="sxs-lookup"><span data-stu-id="5f791-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="5f791-121">Mapu:</span><span class="sxs-lookup"><span data-stu-id="5f791-121">Map:</span></span>  
  
- <span data-ttu-id="5f791-122">0 starý posun, 0 nový posun</span><span class="sxs-lookup"><span data-stu-id="5f791-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="5f791-123">5 starý posun, 10 nových offsetů</span><span class="sxs-lookup"><span data-stu-id="5f791-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="5f791-124">9 starý posun, 20 nových offsetů</span><span class="sxs-lookup"><span data-stu-id="5f791-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="5f791-125">Výsledky:</span><span class="sxs-lookup"><span data-stu-id="5f791-125">Results:</span></span>  
  
- <span data-ttu-id="5f791-126">Staré posun 0, 1, 2, 3 nebo 4 bude mapován na nový posun 0.</span><span class="sxs-lookup"><span data-stu-id="5f791-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="5f791-127">Starý posun 5, 6, 7 nebo 8 bude mapován na nové posun10.</span><span class="sxs-lookup"><span data-stu-id="5f791-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="5f791-128">Starý posun 9 nebo vyšší bude mapován na nový posun 20.</span><span class="sxs-lookup"><span data-stu-id="5f791-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="5f791-129">Nové posun0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 bude mapován na staré posun0.</span><span class="sxs-lookup"><span data-stu-id="5f791-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="5f791-130">Nový posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 bude mapován na starý posun 5.</span><span class="sxs-lookup"><span data-stu-id="5f791-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="5f791-131">Nový posun 20 nebo vyšší bude mapován na staré posun 9.</span><span class="sxs-lookup"><span data-stu-id="5f791-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f791-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f791-132">Requirements</span></span>  
 <span data-ttu-id="5f791-133">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f791-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f791-134">**Záhlaví:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5f791-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="5f791-135">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f791-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f791-136">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f791-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f791-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f791-137">See also</span></span>

- [<span data-ttu-id="5f791-138">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="5f791-138">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="5f791-139">ladění</span><span class="sxs-lookup"><span data-stu-id="5f791-139">Debugging</span></span>](index.md)
