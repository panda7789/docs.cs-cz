---
title: COR_HEAPINFO – struktura
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179313"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="b5c5d-102">COR_HEAPINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="b5c5d-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="b5c5d-103">Obsahuje obecné informace o haldě uvolňování paměti, včetně toho, zda je početovatelný.</span><span class="sxs-lookup"><span data-stu-id="b5c5d-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5c5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5c5d-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b5c5d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b5c5d-105">Members</span></span>  
  
|<span data-ttu-id="b5c5d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b5c5d-106">Member</span></span>|<span data-ttu-id="b5c5d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b5c5d-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="b5c5d-108">`true`pokud jsou platné struktury uvolňování paměti a haldy mohou být uvedeny; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="b5c5d-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="b5c5d-109">Velikost v bajtů ukazatelů na cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="b5c5d-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="b5c5d-110">Počet hromady logické uvolňování paměti v procesu.</span><span class="sxs-lookup"><span data-stu-id="b5c5d-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="b5c5d-111">`TRUE`pokud je povoleno souběžné uvolňování paměti (pozadí); v `FALSE`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="b5c5d-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="b5c5d-112">Člen výčtu [CorDebugGCType,](cordebuggctype-enumeration.md) který označuje, zda je systém uvolňování paměti spuštěn na pracovní stanici nebo na serveru.</span><span class="sxs-lookup"><span data-stu-id="b5c5d-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5c5d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5c5d-113">Remarks</span></span>  
 <span data-ttu-id="b5c5d-114">Instance `COR_HEAPINFO` struktury je vrácena voláním metody [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)</span><span class="sxs-lookup"><span data-stu-id="b5c5d-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="b5c5d-115">Před výčet objektů na haldě uvolňování paměti, `areGCStructuresValid` musíte vždy zkontrolovat pole, aby zajistily, že haldy je ve stavu výčtu.</span><span class="sxs-lookup"><span data-stu-id="b5c5d-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="b5c5d-116">Další informace naleznete v metodě [ICorDebugProcess5::GetGCHeapInformation.](icordebugprocess5-getgcheapinformation-method.md)</span><span class="sxs-lookup"><span data-stu-id="b5c5d-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5c5d-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5c5d-117">Requirements</span></span>  
 <span data-ttu-id="b5c5d-118">**Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5c5d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5c5d-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5c5d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5c5d-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5c5d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5c5d-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5c5d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c5d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5c5d-122">See also</span></span>

- [<span data-ttu-id="b5c5d-123">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="b5c5d-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="b5c5d-124">ladění</span><span class="sxs-lookup"><span data-stu-id="b5c5d-124">Debugging</span></span>](index.md)
