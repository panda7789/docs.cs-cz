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
ms.openlocfilehash: 9a9eb63e681b47f058901b0ff002015baffe6048
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775658"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="8e32f-102">ICorDebugHandleValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e32f-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="8e32f-103">Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8e32f-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8e32f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8e32f-104">Methods</span></span>  
  
|<span data-ttu-id="8e32f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8e32f-105">Method</span></span>|<span data-ttu-id="8e32f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8e32f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8e32f-107">Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="8e32f-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="8e32f-108">Uvolní popisovač odkazovaná tímto objektem `ICorDebugHandleValue` objektu bez explicitně ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8e32f-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="8e32f-109">GetHandleType – metoda</span><span class="sxs-lookup"><span data-stu-id="8e32f-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="8e32f-110">Získá hodnotu cordebughandletype –, který popisuje typ, který odkazuje tento popisovač `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="8e32f-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e32f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e32f-111">Remarks</span></span>  
 <span data-ttu-id="8e32f-112">`ICorDebugReferenceValue` Objektu je ukončit platnost přerušením provádění laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="8e32f-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="8e32f-113">`ICorDebugHandleValue` Udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud je explicitně uvolněn.</span><span class="sxs-lookup"><span data-stu-id="8e32f-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e32f-114">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="8e32f-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e32f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e32f-115">Requirements</span></span>  
 <span data-ttu-id="8e32f-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e32f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e32f-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8e32f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e32f-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e32f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e32f-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e32f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e32f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e32f-120">See also</span></span>

- [<span data-ttu-id="8e32f-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8e32f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
