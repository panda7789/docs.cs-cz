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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffca8e076fe6fe966a9a07ed915a7e76ea06f37c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518069"
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="d35c0-102">COR_HEAPINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="d35c0-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="d35c0-103">Obsahuje obecné informace o haldě uvolňování paměti kolekce, včetně toho, zda je vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="d35c0-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d35c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d35c0-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d35c0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="d35c0-105">Members</span></span>  
  
|<span data-ttu-id="d35c0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="d35c0-106">Member</span></span>|<span data-ttu-id="d35c0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d35c0-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="d35c0-108">`true` Pokud se uvolňování paměti kolekce struktur jsou platné a jsou uvedené haldy; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="d35c0-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="d35c0-109">Velikost v bajtech, ukazatelů na cílové architektuře.</span><span class="sxs-lookup"><span data-stu-id="d35c0-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="d35c0-110">Počet logických uvolňování paměti haldy v procesu.</span><span class="sxs-lookup"><span data-stu-id="d35c0-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="d35c0-111">`TRUE` Pokud souběžné uvolňování paměti (pozadí) je povoleno; v opačném případě `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="d35c0-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="d35c0-112">Člen [cordebuggctype –](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) výčet, který označuje, zda systému uvolňování paměti běží na serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="d35c0-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d35c0-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d35c0-113">Remarks</span></span>  
 <span data-ttu-id="d35c0-114">Instance `COR_HEAPINFO` struktura je vrácený voláním [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d35c0-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="d35c0-115">Před vytváření výčtu objektů na haldě uvolňování paměti, musí vždy zkontrolujte `areGCStructuresValid` pole tak, aby byl haldy ve výčtu stavu.</span><span class="sxs-lookup"><span data-stu-id="d35c0-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="d35c0-116">Další informace najdete v tématu [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d35c0-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d35c0-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d35c0-117">Requirements</span></span>  
 <span data-ttu-id="d35c0-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d35c0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d35c0-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d35c0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d35c0-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d35c0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d35c0-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d35c0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35c0-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d35c0-122">See also</span></span>
- [<span data-ttu-id="d35c0-123">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="d35c0-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="d35c0-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="d35c0-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
