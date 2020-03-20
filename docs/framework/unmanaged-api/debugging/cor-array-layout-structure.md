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
ms.openlocfilehash: ca2d00611a7530dfb0d1c2a27123947bdf69820d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179343"
---
# <a name="cor_array_layout-structure"></a><span data-ttu-id="90dad-102">COR_ARRAY_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="90dad-102">COR_ARRAY_LAYOUT Structure</span></span>
<span data-ttu-id="90dad-103">Obsahuje informace o rozložení objektu pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="90dad-103">Provides information about the layout of an array object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90dad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90dad-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="90dad-105">Členové</span><span class="sxs-lookup"><span data-stu-id="90dad-105">Members</span></span>  
  
|<span data-ttu-id="90dad-106">Člen</span><span class="sxs-lookup"><span data-stu-id="90dad-106">Member</span></span>|<span data-ttu-id="90dad-107">Popis</span><span class="sxs-lookup"><span data-stu-id="90dad-107">Description</span></span>|  
|------------|-----------------|  
|`componentID`|<span data-ttu-id="90dad-108">Identifikátor typu objektů, které pole obsahuje.</span><span class="sxs-lookup"><span data-stu-id="90dad-108">The identifier of the type of objects that the array contains.</span></span>|  
|`componentType`|<span data-ttu-id="90dad-109">Hodnota výčtu CorElementType, která označuje, zda je komponenta odkaz emitovaného, třída hodnoty nebo primitivní.</span><span class="sxs-lookup"><span data-stu-id="90dad-109">A CorElementType enumeration value that indicates whether the component is a garbage collection reference, a value class, or a primitive.</span></span>|  
|`firstElementOffset`|<span data-ttu-id="90dad-110">Posun na první prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="90dad-110">The offset to the first element in the array.</span></span>|  
|`elementSize`|<span data-ttu-id="90dad-111">Velikost každého prvku.</span><span class="sxs-lookup"><span data-stu-id="90dad-111">The size of each element.</span></span>|  
|`countOffset`|<span data-ttu-id="90dad-112">Posun k počtu prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="90dad-112">The offset to the number of elements in the array.</span></span>|  
|`rankSize`|<span data-ttu-id="90dad-113">Velikost pořadí v bajtů.</span><span class="sxs-lookup"><span data-stu-id="90dad-113">The size of the rank, in bytes.</span></span>|  
|`numRanks`|<span data-ttu-id="90dad-114">Počet řad v poli.</span><span class="sxs-lookup"><span data-stu-id="90dad-114">The number of ranks in the array.</span></span>|  
|`rankOffset`|<span data-ttu-id="90dad-115">Posun, při kterém začínají hodnosti.</span><span class="sxs-lookup"><span data-stu-id="90dad-115">The offset at which the ranks start.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90dad-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90dad-116">Remarks</span></span>  
 <span data-ttu-id="90dad-117">Toto `rankSize` pole určuje velikost pořadí ve vícerozměrném poli.</span><span class="sxs-lookup"><span data-stu-id="90dad-117">The `rankSize` field specifies the size of a rank in a multi-dimensional array.</span></span> <span data-ttu-id="90dad-118">Je také přesná i pro jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="90dad-118">It is accurate for single-dimensional arrays as well.</span></span>  
  
 <span data-ttu-id="90dad-119">Hodnota `numRanks` je 1 pro jednorozměrné `N` pole a pro vícerozměrné pole dimenzí. `N`</span><span class="sxs-lookup"><span data-stu-id="90dad-119">The value of `numRanks` is 1 for a single-dimensional array and `N` for a multi-dimensional array of `N` dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90dad-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90dad-120">Requirements</span></span>  
 <span data-ttu-id="90dad-121">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90dad-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90dad-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90dad-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90dad-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90dad-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90dad-124">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90dad-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90dad-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="90dad-125">See also</span></span>

- [<span data-ttu-id="90dad-126">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="90dad-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="90dad-127">ladění</span><span class="sxs-lookup"><span data-stu-id="90dad-127">Debugging</span></span>](index.md)
