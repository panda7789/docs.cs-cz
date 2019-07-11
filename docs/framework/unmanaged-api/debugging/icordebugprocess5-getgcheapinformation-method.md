---
title: ICorDebugProcess5::GetGCHeapInformation – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e94034fcdcd8d86f34c61af30a7729a80c913fac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767349"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="9cb9e-102">ICorDebugProcess5::GetGCHeapInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="9cb9e-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="9cb9e-103">Obsahuje obecné informace o haldě uvolňování paměti kolekce, včetně toho, jestli je aktuálně vyčíslitelná.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cb9e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cb9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cb9e-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="9cb9e-106">[out] Ukazatel [cor_heapinfo –](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) hodnotu, která poskytuje obecné informace o haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cb9e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cb9e-107">Remarks</span></span>  
 <span data-ttu-id="9cb9e-108">`ICorDebugProcess5::GetGCHeapInformation` Metoda musí být volána před výčet haldy nebo jednotlivé haldy oblastech a ujistěte se, že uvolňování paměti kolekce struktur v procesu jsou aktuálně platná.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="9cb9e-109">Haldě uvolňování paměti nelze vás, když probíhá kolekce.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="9cb9e-110">V opačném případě výčet může zachytit struktury kolekce uvolnění paměti, které jsou neplatné.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb9e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cb9e-111">Requirements</span></span>  
 <span data-ttu-id="9cb9e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cb9e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb9e-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cb9e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cb9e-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cb9e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cb9e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb9e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb9e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cb9e-116">See also</span></span>

- [<span data-ttu-id="9cb9e-117">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cb9e-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="9cb9e-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9cb9e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
