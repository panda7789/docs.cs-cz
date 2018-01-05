---
title: "COR_IL_MAP – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_IL_MAP
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_IL_MAP
helpviewer_keywords: COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e2772833d75ced2209896ca37cf6cf37fb965f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corilmap-structure"></a><span data-ttu-id="98bc7-102">COR_IL_MAP – struktura</span><span class="sxs-lookup"><span data-stu-id="98bc7-102">COR_IL_MAP Structure</span></span>
<span data-ttu-id="98bc7-103">Určuje změny v relativní posun funkce.</span><span class="sxs-lookup"><span data-stu-id="98bc7-103">Specifies changes in the relative offset of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98bc7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98bc7-104">Syntax</span></span>  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="98bc7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="98bc7-105">Members</span></span>  
  
|<span data-ttu-id="98bc7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="98bc7-106">Member</span></span>|<span data-ttu-id="98bc7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="98bc7-107">Description</span></span>|  
|------------|-----------------|  
|`oldOffset`|<span data-ttu-id="98bc7-108">Staré Microsoft (MSIL intermediate language) posunuto vzhledem ke začátku funkce.</span><span class="sxs-lookup"><span data-stu-id="98bc7-108">The old Microsoft intermediate language (MSIL) offset relative to the beginning of the function.</span></span>|  
|`newOffset`|<span data-ttu-id="98bc7-109">Nové MSIL posun vzhledem k začátku funkce.</span><span class="sxs-lookup"><span data-stu-id="98bc7-109">The new MSIL offset relative to the beginning of the function.</span></span>|  
|`fAccurate`|<span data-ttu-id="98bc7-110">`true`Pokud mapování se označuje jako přesné; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="98bc7-110">`true` if the mapping is known to be accurate; otherwise, `false`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98bc7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98bc7-111">Remarks</span></span>  
 <span data-ttu-id="98bc7-112">Formát mapy je následující: ladicí program předpokládat, že `oldOffset` odkazuje na MSIL posun v rámci kód MSIL původní, beze změny.</span><span class="sxs-lookup"><span data-stu-id="98bc7-112">The format of the map is as follows: The debugger will assume that `oldOffset` refers to an MSIL offset within the original, unmodified MSIL code.</span></span> <span data-ttu-id="98bc7-113">`newOffset` Parametr odkazuje na odpovídající posun MSIL nové, instrumentovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="98bc7-113">The `newOffset` parameter refers to the corresponding MSIL offset within the new, instrumented code.</span></span>  
  
 <span data-ttu-id="98bc7-114">Pro krokování s fungovalo správně, musí být splněny následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="98bc7-114">For stepping to work properly, the following requirements should be met:</span></span>  
  
-   <span data-ttu-id="98bc7-115">Mapy by měly být seřazeny ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="98bc7-115">The map should be sorted in ascending order.</span></span>  
  
-   <span data-ttu-id="98bc7-116">Instrumentované MSIL kód by neměl přeuspořádány.</span><span class="sxs-lookup"><span data-stu-id="98bc7-116">Instrumented MSIL code should not be reordered.</span></span>  
  
-   <span data-ttu-id="98bc7-117">Původní kód MSIL by se neměly odebírat.</span><span class="sxs-lookup"><span data-stu-id="98bc7-117">Original MSIL code should not be removed.</span></span>  
  
-   <span data-ttu-id="98bc7-118">Mapy by měla obsahovat položky pro všechny body sekvence ze souboru databáze (PDB) program mapování.</span><span class="sxs-lookup"><span data-stu-id="98bc7-118">The map should include entries to map all the sequence points from the program database (PDB) file.</span></span>  
  
 <span data-ttu-id="98bc7-119">Mapy není interpolovat položky.</span><span class="sxs-lookup"><span data-stu-id="98bc7-119">The map does not interpolate missing entries.</span></span> <span data-ttu-id="98bc7-120">Následující příklad ukazuje mapu a jeho výsledky.</span><span class="sxs-lookup"><span data-stu-id="98bc7-120">The following example shows a map and its results.</span></span>  
  
 <span data-ttu-id="98bc7-121">Mapování:</span><span class="sxs-lookup"><span data-stu-id="98bc7-121">Map:</span></span>  
  
-   <span data-ttu-id="98bc7-122">původní posun 0, 0 nové posun</span><span class="sxs-lookup"><span data-stu-id="98bc7-122">0 old offset, 0 new offset</span></span>  
  
-   <span data-ttu-id="98bc7-123">původní offset 5, 10 nové posun</span><span class="sxs-lookup"><span data-stu-id="98bc7-123">5 old offset, 10 new offset</span></span>  
  
-   <span data-ttu-id="98bc7-124">9 staré offset, 20 nové posunutí</span><span class="sxs-lookup"><span data-stu-id="98bc7-124">9 old offset, 20 new offset</span></span>  
  
 <span data-ttu-id="98bc7-125">Výsledky:</span><span class="sxs-lookup"><span data-stu-id="98bc7-125">Results:</span></span>  
  
-   <span data-ttu-id="98bc7-126">Původní posun 0, 1, 2, 3 nebo 4 budou mapována na nový posun 0.</span><span class="sxs-lookup"><span data-stu-id="98bc7-126">An old offset of 0, 1, 2, 3, or 4 will be mapped to a new offset of 0.</span></span>  
  
-   <span data-ttu-id="98bc7-127">Původní posun 5, 6, 7 nebo 8 budou mapována na nový posun 10.</span><span class="sxs-lookup"><span data-stu-id="98bc7-127">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
-   <span data-ttu-id="98bc7-128">Původní posun 9 nebo vyšší budou mapována na nový posun 20.</span><span class="sxs-lookup"><span data-stu-id="98bc7-128">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
-   <span data-ttu-id="98bc7-129">Nové posun 0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 budou mapována na staré posunu 0.</span><span class="sxs-lookup"><span data-stu-id="98bc7-129">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
-   <span data-ttu-id="98bc7-130">Nové posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 budou mapována na staré posun 5.</span><span class="sxs-lookup"><span data-stu-id="98bc7-130">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
-   <span data-ttu-id="98bc7-131">Nové posun 20 nebo vyšší budou mapována na staré posun 9.</span><span class="sxs-lookup"><span data-stu-id="98bc7-131">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98bc7-132">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98bc7-132">Requirements</span></span>  
 <span data-ttu-id="98bc7-133">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98bc7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98bc7-134">**Záhlaví:** CorDebug.idl, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="98bc7-134">**Header:** CorDebug.idl, CorProf.idl</span></span>  
  
 <span data-ttu-id="98bc7-135">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98bc7-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98bc7-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98bc7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98bc7-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="98bc7-137">See Also</span></span>  
 [<span data-ttu-id="98bc7-138">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="98bc7-138">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="98bc7-139">Ladění</span><span class="sxs-lookup"><span data-stu-id="98bc7-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
