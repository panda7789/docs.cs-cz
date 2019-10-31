---
title: ICorDebugProcess::ClearCurrentException – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: 37a7d8fa4439d52db3cddfff22ac6580b19af58a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128917"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="619f3-102">ICorDebugProcess::ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="619f3-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="619f3-103">Vymaže aktuální nespravovanou výjimku na daném vlákně.</span><span class="sxs-lookup"><span data-stu-id="619f3-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="619f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="619f3-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="619f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="619f3-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="619f3-106">pro ID vlákna, na kterém bude vymazána aktuální nespravovanou výjimka.</span><span class="sxs-lookup"><span data-stu-id="619f3-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="619f3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="619f3-107">Remarks</span></span>  
 <span data-ttu-id="619f3-108">Před voláním metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) volejte tuto metodu, pokud vlákno oznámilo nespravovanou výjimku, kterou by měl ignorovat laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="619f3-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="619f3-109">Tím se v daném vláknu vymažou nedokončené události v pásmu (IB) i mimo pásmo (OOB).</span><span class="sxs-lookup"><span data-stu-id="619f3-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="619f3-110">Všechny zarážky OOB a výjimky s jedním krokem se automaticky vymažou.</span><span class="sxs-lookup"><span data-stu-id="619f3-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="619f3-111">K zachycení aktuální spravované výjimky ve vlákně použijte [ICorDebugThread2:: InterceptCurrentException –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="619f3-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="619f3-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="619f3-112">Requirements</span></span>  
 <span data-ttu-id="619f3-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="619f3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="619f3-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="619f3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="619f3-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="619f3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="619f3-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="619f3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
