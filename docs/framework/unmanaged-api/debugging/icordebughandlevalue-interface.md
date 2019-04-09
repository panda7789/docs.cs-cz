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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117440"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="33a08-102">ICorDebugHandleValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33a08-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="33a08-103">Podtřída ICorDebugReferenceValue, která představuje referenční hodnotu, do které ladicí program vytvořil popisovač pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="33a08-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33a08-104">Metody</span><span class="sxs-lookup"><span data-stu-id="33a08-104">Methods</span></span>  
  
|<span data-ttu-id="33a08-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="33a08-105">Method</span></span>|<span data-ttu-id="33a08-106">Popis</span><span class="sxs-lookup"><span data-stu-id="33a08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33a08-107">Dispose – metoda</span><span class="sxs-lookup"><span data-stu-id="33a08-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="33a08-108">Uvolní popisovač odkazovaná tímto objektem `ICorDebugHandleValue` objektu bez explicitně ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="33a08-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="33a08-109">GetHandleType – metoda</span><span class="sxs-lookup"><span data-stu-id="33a08-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="33a08-110">Získá hodnotu cordebughandletype –, který popisuje typ, který odkazuje tento popisovač `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="33a08-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33a08-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33a08-111">Remarks</span></span>  
 <span data-ttu-id="33a08-112">`ICorDebugReferenceValue` Objektu je ukončit platnost přerušením provádění laděného kódu.</span><span class="sxs-lookup"><span data-stu-id="33a08-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="33a08-113">`ICorDebugHandleValue` Udržuje svůj odkaz prostřednictvím přerušení a pokračování, dokud je explicitně uvolněn.</span><span class="sxs-lookup"><span data-stu-id="33a08-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33a08-114">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="33a08-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33a08-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33a08-115">Requirements</span></span>  
 <span data-ttu-id="33a08-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33a08-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a08-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33a08-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33a08-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33a08-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="33a08-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="33a08-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33a08-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33a08-120">See also</span></span>

- [<span data-ttu-id="33a08-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33a08-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
