---
title: ICorDebugHandleValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 94472e84b73cdffe09505088b1e7fbc20a209bc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138479"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="a1f1f-102">ICorDebugHandleValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1f1f-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="a1f1f-103">Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1f1f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1f1f-104">Methods</span></span>  
  
|<span data-ttu-id="a1f1f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1f1f-105">Method</span></span>|<span data-ttu-id="a1f1f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a1f1f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1f1f-107">Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="a1f1f-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="a1f1f-108">Uvolňuje popisovač, na který odkazuje tento objekt `ICorDebugHandleValue`, bez explicitního uvolnění ukazatele rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="a1f1f-109">GetHandleType – metoda</span><span class="sxs-lookup"><span data-stu-id="a1f1f-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="a1f1f-110">Získá hodnotu CorDebugHandleType –, která popisuje druh popisovače, na který odkazuje tento `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1f1f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1f1f-111">Remarks</span></span>  
 <span data-ttu-id="a1f1f-112">Objekt `ICorDebugReferenceValue` je po přerušení v provádění laděného kódu neplatný.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="a1f1f-113">`ICorDebugHandleValue` udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud není explicitně uvolněn.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1f1f-114">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a1f1f-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f1f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1f1f-115">Requirements</span></span>  
 <span data-ttu-id="a1f1f-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f1f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f1f-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a1f1f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1f1f-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a1f1f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1f1f-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f1f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f1f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1f1f-120">See also</span></span>

- [<span data-ttu-id="a1f1f-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a1f1f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
