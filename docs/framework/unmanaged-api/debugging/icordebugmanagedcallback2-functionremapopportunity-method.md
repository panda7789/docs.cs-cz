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
ms.openlocfilehash: bc6543b46200dd611e13bdf55aabfabd8302e70a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793337"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a><span data-ttu-id="893c6-102">ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda</span><span class="sxs-lookup"><span data-stu-id="893c6-102">ICorDebugManagedCallback2::FunctionRemapOpportunity Method</span></span>
<span data-ttu-id="893c6-103">Oznamuje ladicímu programu, že provádění kódu dosáhlo bodu sekvence ve starší verzi upravované funkce.</span><span class="sxs-lookup"><span data-stu-id="893c6-103">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="893c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="893c6-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="893c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="893c6-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="893c6-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující upravenou funkci.</span><span class="sxs-lookup"><span data-stu-id="893c6-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="893c6-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém byla zjištěna zarážka přemapování.</span><span class="sxs-lookup"><span data-stu-id="893c6-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pOldFunction`  
 <span data-ttu-id="893c6-108">pro Ukazatel na objekt ICorDebugFunction, který představuje verzi funkce, která je aktuálně spuštěna ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="893c6-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function that is currently running on the thread.</span></span>  
  
 `pNewFunction`  
 <span data-ttu-id="893c6-109">pro Ukazatel na objekt ICorDebugFunction, který představuje nejnovější verzi funkce.</span><span class="sxs-lookup"><span data-stu-id="893c6-109">[in] A pointer to an ICorDebugFunction object that represents the latest version of the function.</span></span>  
  
 `oldILOffset`  
 <span data-ttu-id="893c6-110">pro Posun jazyka MSIL (Microsoft Intermediate Language) ukazatele na instrukci ve staré verzi funkce.</span><span class="sxs-lookup"><span data-stu-id="893c6-110">[in] The Microsoft intermediate language (MSIL) offset of the instruction pointer in the old version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="893c6-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="893c6-111">Remarks</span></span>  
 <span data-ttu-id="893c6-112">Toto zpětné volání umožňuje ladicímu programu možnost přemapovat ukazatel na jeho správné místo v nové verzi zadané funkce voláním metody [ICorDebugILFrame2:: RemapFunction](icordebugilframe2-remapfunction-method.md) .</span><span class="sxs-lookup"><span data-stu-id="893c6-112">This callback gives the debugger an opportunity to remap the instruction pointer to its proper place in the new version of the specified function by calling the [ICorDebugILFrame2::RemapFunction](icordebugilframe2-remapfunction-method.md) method.</span></span> <span data-ttu-id="893c6-113">Pokud ladicí program nevolá `RemapFunction` před voláním metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , modul runtime bude pokračovat v provádění starého kódu a vyvolá jiné zpětné volání `FunctionRemapOpportunity` v dalším bodu sekvence.</span><span class="sxs-lookup"><span data-stu-id="893c6-113">If the debugger does not call `RemapFunction` before calling the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method, the runtime will continue to execute the old code and will fire another `FunctionRemapOpportunity` callback at the next sequence point.</span></span>  
  
 <span data-ttu-id="893c6-114">Toto zpětné volání bude vyvoláno pro každý rámec, který spouští starší verzi dané funkce, dokud ladicí program nevrátí S_OK.</span><span class="sxs-lookup"><span data-stu-id="893c6-114">This callback will be invoked for every frame that is executing an older version of the given function until the debugger returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="893c6-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="893c6-115">Requirements</span></span>  
 <span data-ttu-id="893c6-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="893c6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="893c6-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="893c6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="893c6-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="893c6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="893c6-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="893c6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="893c6-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="893c6-120">See also</span></span>

- [<span data-ttu-id="893c6-121">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="893c6-121">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="893c6-122">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="893c6-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
