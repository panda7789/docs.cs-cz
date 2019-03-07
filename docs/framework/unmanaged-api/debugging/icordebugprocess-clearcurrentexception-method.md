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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f014f9213a4b9a2d5119af9a6dceebb9a9d54b52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473462"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="4bb8b-102">ICorDebugProcess::ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="4bb8b-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="4bb8b-103">Vymaže aktuální nespravované výjimky na dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="4bb8b-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bb8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bb8b-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bb8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bb8b-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="4bb8b-106">[in] ID vlákna, na kterém aktuální nespravované výjimky se vymažou.</span><span class="sxs-lookup"><span data-stu-id="4bb8b-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bb8b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4bb8b-107">Remarks</span></span>  
 <span data-ttu-id="4bb8b-108">Volání před voláním této metody [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) když vlákno ohlásil nespravované výjimky, které mají být ignorovány ladicím procesem.</span><span class="sxs-lookup"><span data-stu-id="4bb8b-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="4bb8b-109">Tato akce vymaže nezpracovaných integrovaných (i b) i out-of-band (OOB) události v daném vláknu.</span><span class="sxs-lookup"><span data-stu-id="4bb8b-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="4bb8b-110">Všechny OOB zarážky a krokování výjimky jsou automaticky vymazány.</span><span class="sxs-lookup"><span data-stu-id="4bb8b-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="4bb8b-111">Použití [icordebugthread2::interceptcurrentexception –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) zachytit aktuální výjimku ve vlákně spravovaných.</span><span class="sxs-lookup"><span data-stu-id="4bb8b-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bb8b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4bb8b-112">Requirements</span></span>  
 <span data-ttu-id="4bb8b-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bb8b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bb8b-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bb8b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bb8b-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bb8b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bb8b-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bb8b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
