---
title: "ICorDebugManagedCallback2::FunctionRemapComplete – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapComplete
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 52c7ead9091754d4355880befe6a8a11b3cc5eaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="5aa05-102">ICorDebugManagedCallback2::FunctionRemapComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="5aa05-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="5aa05-103">Upozorní ladicí program, že provádění kódu přepnul na novou verzi upravená funkce.</span><span class="sxs-lookup"><span data-stu-id="5aa05-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aa05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5aa05-104">Syntax</span></span>  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5aa05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5aa05-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="5aa05-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující upravená funkce.</span><span class="sxs-lookup"><span data-stu-id="5aa05-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5aa05-107">[v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, na kterém byl zjištěn bod přemapování přerušení.</span><span class="sxs-lookup"><span data-stu-id="5aa05-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="5aa05-108">[v] Ukazatel na ICorDebugFunction objekt, který představuje verzi funkce aktuálně spuštěné na vlákno.</span><span class="sxs-lookup"><span data-stu-id="5aa05-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5aa05-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5aa05-109">Remarks</span></span>  
 <span data-ttu-id="5aa05-110">Tento zpětného volání dává příležitost znovu vytvořit všechny steppers, které dříve existoval ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="5aa05-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aa05-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5aa05-111">Requirements</span></span>  
 <span data-ttu-id="5aa05-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5aa05-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aa05-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5aa05-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5aa05-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5aa05-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5aa05-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aa05-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa05-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5aa05-116">See Also</span></span>  
 [<span data-ttu-id="5aa05-117">ICorDebugManagedCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5aa05-117">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="5aa05-118">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5aa05-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
