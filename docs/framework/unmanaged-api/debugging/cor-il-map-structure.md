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
ms.openlocfilehash: e6d8023c7ac6d917c9df40fb18316ddc12df5ec1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609423"
---
# <a name="corilmap-structure"></a><span data-ttu-id="cd011-102">COR_IL_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="cd011-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="cd011-103">Určuje změny v relativním posunem funkce.</span><span class="sxs-lookup"><span data-stu-id="cd011-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd011-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd011-104">Syntax</span></span>  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="cd011-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cd011-105">Members</span></span>  
  
|<span data-ttu-id="cd011-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cd011-106">Member</span></span>|<span data-ttu-id="cd011-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cd011-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="cd011-108">Stará Microsoft intermediate language (MSIL) posun vzhledem k začátku funkci.</span><span class="sxs-lookup"><span data-stu-id="cd011-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="cd011-109">Nový jazyk MSIL posun vzhledem k začátku funkci.</span><span class="sxs-lookup"><span data-stu-id="cd011-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="cd011-110">`true` Pokud mapování je znám jako přesné; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="cd011-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd011-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd011-111">Remarks</span></span>  
 <span data-ttu-id="cd011-112">Formát mapování je následujícím způsobem: Ladicí program se předpokládá, že `oldOffset` odkazuje na MSIL posun v rámci původní verzí bez úprav kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="cd011-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="cd011-113">`newOffset` Parametr odkazuje na odpovídající jazyk MSIL posun v rámci nové instrumentované kódu.</span><span class="sxs-lookup"><span data-stu-id="cd011-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="cd011-114">Pro krokování fungovalo správně, musí být splněny následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="cd011-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
- <span data-ttu-id="cd011-115">Na mapě mají být řazeny ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd011-115">The map should be sorted in ascending order.</span></span>  
  
- <span data-ttu-id="cd011-116">By neměl být přeuspořádány instrumentované kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="cd011-116">Instrumented MSIL code should not be reordered.</span></span>  
  
- <span data-ttu-id="cd011-117">Původní kód jazyka MSIL by se neměly odebírat.</span><span class="sxs-lookup"><span data-stu-id="cd011-117">Original MSIL code should not be removed.</span></span>  
  
- <span data-ttu-id="cd011-118">Na mapě by měl obsahovat záznamy pro všechny body posloupnosti ze souboru databáze (PDB) programu mapování.</span><span class="sxs-lookup"><span data-stu-id="cd011-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="cd011-119">Mapa není interpolovat chybějící položky.</span><span class="sxs-lookup"><span data-stu-id="cd011-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="cd011-120">Následující příklad ukazuje, mapy a jeho výsledky.</span><span class="sxs-lookup"><span data-stu-id="cd011-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="cd011-121">Mapy:</span><span class="sxs-lookup"><span data-stu-id="cd011-121">Map:</span></span>  
  
- <span data-ttu-id="cd011-122">Posun 0 starý, nový posun 0</span><span class="sxs-lookup"><span data-stu-id="cd011-122">0 old offset, 0 new offset</span></span>  
  
- <span data-ttu-id="cd011-123">staré posun 5, 10 nových posun</span><span class="sxs-lookup"><span data-stu-id="cd011-123">5 old offset, 10 new offset</span></span>  
  
- <span data-ttu-id="cd011-124">staré posun 9, 20 nové posun</span><span class="sxs-lookup"><span data-stu-id="cd011-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="cd011-125">Počet výsledků:</span><span class="sxs-lookup"><span data-stu-id="cd011-125">Results:</span></span>  
  
- <span data-ttu-id="cd011-126">Staré posun 0, 1, 2, 3 nebo 4 se namapují na nové posun 0.</span><span class="sxs-lookup"><span data-stu-id="cd011-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
- <span data-ttu-id="cd011-127">Posun staré 5, 6, 7 nebo 8 se namapují na nové posun 10.</span><span class="sxs-lookup"><span data-stu-id="cd011-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
- <span data-ttu-id="cd011-128">Staré posun 9 nebo vyšší se namapují na nové posun 20.</span><span class="sxs-lookup"><span data-stu-id="cd011-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
- <span data-ttu-id="cd011-129">Nové posun 0, 1, 2, 3, 4, 5, 6, 7, 8 a 9 se namapují na staré posun 0.</span><span class="sxs-lookup"><span data-stu-id="cd011-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
- <span data-ttu-id="cd011-130">Nové posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 se namapují na staré posun 5.</span><span class="sxs-lookup"><span data-stu-id="cd011-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
- <span data-ttu-id="cd011-131">Nové posun 20 nebo vyšší se namapují na staré posun 9.</span><span class="sxs-lookup"><span data-stu-id="cd011-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd011-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd011-132">Requirements</span></span>  
 <span data-ttu-id="cd011-133">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd011-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd011-134">**Záhlaví:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="cd011-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="cd011-135">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd011-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd011-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd011-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd011-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd011-137">See also</span></span>

- [<span data-ttu-id="cd011-138">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="cd011-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="cd011-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="cd011-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
