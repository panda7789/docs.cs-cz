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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dddc1665dff5c1a0629d25aa99066ce6eeca94a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981436"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="59ba1-102">ICorDebugHandleValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59ba1-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="59ba1-103">Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="59ba1-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59ba1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="59ba1-104">Methods</span></span>  
  
|<span data-ttu-id="59ba1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="59ba1-105">Method</span></span>|<span data-ttu-id="59ba1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="59ba1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59ba1-107">Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="59ba1-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="59ba1-108">Uvolní popisovač odkazovaná tímto objektem `ICorDebugHandleValue` objektu bez explicitně ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="59ba1-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="59ba1-109">GetHandleType – metoda</span><span class="sxs-lookup"><span data-stu-id="59ba1-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="59ba1-110">Získá hodnotu cordebughandletype –, který popisuje typ, který odkazuje tento popisovač `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="59ba1-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ba1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59ba1-111">Remarks</span></span>  
 <span data-ttu-id="59ba1-112">`ICorDebugReferenceValue` Objektu je ukončit platnost přerušením provádění laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="59ba1-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="59ba1-113">`ICorDebugHandleValue` Udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud je explicitně uvolněn.</span><span class="sxs-lookup"><span data-stu-id="59ba1-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59ba1-114">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="59ba1-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ba1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59ba1-115">Requirements</span></span>  
 <span data-ttu-id="59ba1-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ba1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ba1-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59ba1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59ba1-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59ba1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59ba1-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59ba1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ba1-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59ba1-120">See also</span></span>
- [<span data-ttu-id="59ba1-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="59ba1-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
