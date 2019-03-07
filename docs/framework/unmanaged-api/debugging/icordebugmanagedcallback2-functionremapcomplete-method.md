---
title: ICorDebugManagedCallback2::FunctionRemapComplete – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f4c9b6afd9b0a7a43c279c9a070740100d8f86
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478619"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="9dfe1-102">ICorDebugManagedCallback2::FunctionRemapComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="9dfe1-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="9dfe1-103">Upozorní ladicího programu, že spuštění kódu se přepnulo na novou verzi funkce se upravila.</span><span class="sxs-lookup"><span data-stu-id="9dfe1-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dfe1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dfe1-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dfe1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9dfe1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9dfe1-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující funkce se upravila.</span><span class="sxs-lookup"><span data-stu-id="9dfe1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="9dfe1-107">[in] Ukazatel na objekt icordebugthread –, který představuje vlákno, na kterém byla zjištěna zarážka přemapování.</span><span class="sxs-lookup"><span data-stu-id="9dfe1-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="9dfe1-108">[in] Ukazatel na objekt ICorDebugFunction, který představuje verzi funkce aktuálně spuštěné vlákno.</span><span class="sxs-lookup"><span data-stu-id="9dfe1-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dfe1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9dfe1-109">Remarks</span></span>  
 <span data-ttu-id="9dfe1-110">Toto zpětné volání umožní ladicího programu znovu vytvořit všechny prvky krokování, které dříve existoval.</span><span class="sxs-lookup"><span data-stu-id="9dfe1-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dfe1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9dfe1-111">Requirements</span></span>  
 <span data-ttu-id="9dfe1-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dfe1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dfe1-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9dfe1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dfe1-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dfe1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dfe1-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dfe1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dfe1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9dfe1-116">See also</span></span>
- [<span data-ttu-id="9dfe1-117">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9dfe1-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="9dfe1-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9dfe1-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
