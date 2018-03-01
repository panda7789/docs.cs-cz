---
title: "ICorDebugProcess::ClearCurrentException – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 905ade7e5c44861b4ad6e7eb57fe7d3e3e9e3002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="eed0e-102">ICorDebugProcess::ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="eed0e-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="eed0e-103">Vymaže aktuální nespravované výjimky na dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="eed0e-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eed0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eed0e-104">Syntax</span></span>  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eed0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eed0e-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="eed0e-106">[v] ID podprocesu, na kterém se vymaže aktuální nespravované výjimky.</span><span class="sxs-lookup"><span data-stu-id="eed0e-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eed0e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eed0e-107">Remarks</span></span>  
 <span data-ttu-id="eed0e-108">Volat tuto metodu před voláním [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) při vlákno ohlásil nespravované výjimka, která má být ignorována ladění.</span><span class="sxs-lookup"><span data-stu-id="eed0e-108">Call this method before calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="eed0e-109">Tímto dojde k vymazání nezpracovaných integrované (IB) i out-of-band události (OOB) na dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="eed0e-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="eed0e-110">Všechny OOB zarážky a krokování výjimky jsou automaticky vymazány.</span><span class="sxs-lookup"><span data-stu-id="eed0e-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="eed0e-111">Použití [icordebugthread2::interceptcurrentexception –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) zachytávat aktuální spravované výjimky na vlákno.</span><span class="sxs-lookup"><span data-stu-id="eed0e-111">Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eed0e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eed0e-112">Requirements</span></span>  
 <span data-ttu-id="eed0e-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eed0e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eed0e-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eed0e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eed0e-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eed0e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eed0e-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eed0e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
