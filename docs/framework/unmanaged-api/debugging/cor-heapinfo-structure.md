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
ms.openlocfilehash: b6fd3682290c9752125aed7b9663c6704ade25de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132325"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="638fd-102">COR_HEAPINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="638fd-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="638fd-103">Poskytuje obecné informace o haldě uvolňování paměti, včetně toho, zda je vyčíslitelné.</span><span class="sxs-lookup"><span data-stu-id="638fd-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="638fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="638fd-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="638fd-105">Členové</span><span class="sxs-lookup"><span data-stu-id="638fd-105">Members</span></span>  
  
|<span data-ttu-id="638fd-106">Člen</span><span class="sxs-lookup"><span data-stu-id="638fd-106">Member</span></span>|<span data-ttu-id="638fd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="638fd-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="638fd-108">`true`, zda jsou struktury uvolňování paměti platné a lze vytvořit výčet haldy; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="638fd-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="638fd-109">Velikost ukazatelů v cílové architektuře v bajtech.</span><span class="sxs-lookup"><span data-stu-id="638fd-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="638fd-110">Počet hald logických uvolňování paměti v procesu.</span><span class="sxs-lookup"><span data-stu-id="638fd-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="638fd-111">`TRUE`, pokud je povolené shromažďování paměti souběžného (na pozadí); v opačném případě `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="638fd-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="638fd-112">Člen výčtu [CorDebugGCType –](cordebuggctype-enumeration.md) , který označuje, zda je systém uvolňování paměti spuštěn na pracovní stanici nebo serveru.</span><span class="sxs-lookup"><span data-stu-id="638fd-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="638fd-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="638fd-113">Remarks</span></span>  
 <span data-ttu-id="638fd-114">Instance `COR_HEAPINFO` struktury je vrácena voláním metody [ICorDebugProcess5:: GetGCHeapInformation –](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="638fd-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="638fd-115">Před vytvořením výčtu objektů v haldě uvolňování paměti je vždy nutné zaškrtnout pole `areGCStructuresValid`, aby se zajistilo, že je halda ve výčtovém stavu.</span><span class="sxs-lookup"><span data-stu-id="638fd-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="638fd-116">Další informace naleznete v tématu metoda [ICorDebugProcess5:: GetGCHeapInformation –](icordebugprocess5-getgcheapinformation-method.md) .</span><span class="sxs-lookup"><span data-stu-id="638fd-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="638fd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="638fd-117">Requirements</span></span>  
 <span data-ttu-id="638fd-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="638fd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="638fd-119">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="638fd-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="638fd-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="638fd-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="638fd-121">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="638fd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638fd-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="638fd-122">See also</span></span>

- [<span data-ttu-id="638fd-123">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="638fd-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="638fd-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="638fd-124">Debugging</span></span>](index.md)
