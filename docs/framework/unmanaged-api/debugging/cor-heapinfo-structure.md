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
ms.openlocfilehash: 8fb1ae367c30bb038bfe25961e91f02f172f486c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405753"
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="ea2ba-102">COR_HEAPINFO – struktura</span><span class="sxs-lookup"><span data-stu-id="ea2ba-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="ea2ba-103">Poskytuje obecné informace o kolekci halda paměti, včetně toho, jestli je vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="ea2ba-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea2ba-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="ea2ba-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ea2ba-105">Members</span></span>  
  
|<span data-ttu-id="ea2ba-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ea2ba-106">Member</span></span>|<span data-ttu-id="ea2ba-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ea2ba-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="ea2ba-108">`true` Pokud jsou platné struktury kolekce paměti a mohou být uvedené halda; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="ea2ba-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="ea2ba-109">Velikost v bajtech, ukazatelů na cílové architektury.</span><span class="sxs-lookup"><span data-stu-id="ea2ba-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="ea2ba-110">Počet logických uvolňování paměti haldách v procesu.</span><span class="sxs-lookup"><span data-stu-id="ea2ba-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="ea2ba-111">`TRUE` Pokud je to souběžné uvolňování paměti (pozadí) je povoleno; v opačném `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="ea2ba-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="ea2ba-112">Člen [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) výčtu, která určuje, zda má systém uvolňování běží na pracovní stanici nebo na serveru.</span><span class="sxs-lookup"><span data-stu-id="ea2ba-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea2ba-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea2ba-113">Remarks</span></span>  
 <span data-ttu-id="ea2ba-114">Instance `COR_HEAPINFO` struktura vrátí volání [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ea2ba-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="ea2ba-115">Před vytváření výčtu objektů v haldě kolekce paměti, je nutné vždy zkontrolovat `areGCStructuresValid` pole zajistit, že halda je ve stavu vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="ea2ba-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="ea2ba-116">Další informace najdete v tématu [icordebugprocess5::getgcheapinformation –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ea2ba-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea2ba-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea2ba-117">Requirements</span></span>  
 <span data-ttu-id="ea2ba-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea2ba-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea2ba-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea2ba-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea2ba-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea2ba-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea2ba-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea2ba-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2ba-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea2ba-122">See Also</span></span>  
 [<span data-ttu-id="ea2ba-123">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="ea2ba-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="ea2ba-124">Ladění</span><span class="sxs-lookup"><span data-stu-id="ea2ba-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
