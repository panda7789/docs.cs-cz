---
title: COR_ARRAY_LAYOUT – struktura
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3a5a5bb26912c87cdf37ba0d8f0cee1cf1ffa97
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142009"
---
# <a name="corarraylayout-structure"></a><span data-ttu-id="5bd56-102">COR_ARRAY_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="5bd56-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="5bd56-103">Poskytuje informace o rozložení objektu array v paměti.</span><span class="sxs-lookup"><span data-stu-id="5bd56-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bd56-104">Syntax</span></span>  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="5bd56-105">Členové</span><span class="sxs-lookup"><span data-stu-id="5bd56-105">Members</span></span>  
  
|<span data-ttu-id="5bd56-106">Člen</span><span class="sxs-lookup"><span data-stu-id="5bd56-106">Member</span></span>|<span data-ttu-id="5bd56-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5bd56-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="5bd56-108">Identifikátor typu objektů, které obsahuje pole.</span><span class="sxs-lookup"><span data-stu-id="5bd56-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="5bd56-109">Corelementtype – hodnotu výčtu, která určuje, zda je součást odkaz kolekce uvolnění paměti, hodnotová třída nebo jednoduchého typu.</span><span class="sxs-lookup"><span data-stu-id="5bd56-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="5bd56-110">Posun na první prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="5bd56-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="5bd56-111">Velikost jednotlivých prvků.</span><span class="sxs-lookup"><span data-stu-id="5bd56-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="5bd56-112">Posun do počtu prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="5bd56-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="5bd56-113">Velikost pořadí, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="5bd56-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="5bd56-114">Číslo pořadí v poli.</span><span class="sxs-lookup"><span data-stu-id="5bd56-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="5bd56-115">Posun, ve kterém je pořadí spuštění.</span><span class="sxs-lookup"><span data-stu-id="5bd56-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bd56-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5bd56-116">Remarks</span></span>  
 <span data-ttu-id="5bd56-117">`rankSize` Pole určuje velikost pořadí v vícerozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="5bd56-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="5bd56-118">Je přesné pro také jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="5bd56-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="5bd56-119">Hodnota `numRanks` 1 pro jednorozměrné pole a `N` pro vícerozměrná pole `N` dimenze.</span><span class="sxs-lookup"><span data-stu-id="5bd56-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bd56-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5bd56-120">Requirements</span></span>  
 <span data-ttu-id="5bd56-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bd56-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bd56-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bd56-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bd56-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bd56-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bd56-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bd56-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd56-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bd56-125">See also</span></span>

- [<span data-ttu-id="5bd56-126">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="5bd56-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="5bd56-127">Ladění</span><span class="sxs-lookup"><span data-stu-id="5bd56-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
