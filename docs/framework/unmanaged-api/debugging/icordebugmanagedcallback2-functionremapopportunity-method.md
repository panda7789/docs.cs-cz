---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24f058ff11a1155aa53a1d1f222ff1230c1c23e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760983"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="11e05-102">ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda</span><span class="sxs-lookup"><span data-stu-id="11e05-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="11e05-103">Upozorní ladicího programu, že spuštění kódu bylo dosaženo bodu sekvence. ve starší verzi funkce se upravila.</span><span class="sxs-lookup"><span data-stu-id="11e05-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11e05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11e05-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11e05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11e05-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="11e05-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující funkce se upravila.</span><span class="sxs-lookup"><span data-stu-id="11e05-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="11e05-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, na kterém byla zjištěna zarážka přemapování.</span><span class="sxs-lookup"><span data-stu-id="11e05-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="11e05-108">[in] Ukazatel na objekt ICorDebugFunction, který představuje verzi funkce, která je aktuálně spuštěna ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="11e05-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="11e05-109">[in] Ukazatel na objekt ICorDebugFunction, který představuje nejnovější funkce.</span><span class="sxs-lookup"><span data-stu-id="11e05-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="11e05-110">[in] Posun Microsoft intermediate language (MSIL) v původní verzi funkce ukazatele na instrukci.</span><span class="sxs-lookup"><span data-stu-id="11e05-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11e05-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11e05-111">Remarks</span></span>  
 <span data-ttu-id="11e05-112">Toto zpětné volání poskytuje ladicího programu příležitost k přemapování ukazatele na instrukci na správné místo v nové verzi zadanou funkci pomocí volání [icordebugilframe2::remapfunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="11e05-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="11e05-113">Pokud ladicí program nevolá `RemapFunction` před voláním [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody, modul runtime bude pokračovat na starý kód spustit a bude platit další `FunctionRemapOpportunity` zpětného volání na další bod sekvence.</span><span class="sxs-lookup"><span data-stu-id="11e05-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="11e05-114">Toto zpětné volání bude volána pro každý snímek, který spouští starší verzi danou funkci dokud ladicí program vrátí hodnotu S_OK.</span><span class="sxs-lookup"><span data-stu-id="11e05-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11e05-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11e05-115">Requirements</span></span>  
 <span data-ttu-id="11e05-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11e05-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11e05-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11e05-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11e05-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11e05-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11e05-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11e05-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e05-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11e05-120">See also</span></span>

- [<span data-ttu-id="11e05-121">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11e05-121">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="11e05-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11e05-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
