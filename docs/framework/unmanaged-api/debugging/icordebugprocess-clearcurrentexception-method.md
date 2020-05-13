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
ms.openlocfilehash: b8d20de990ff4a27a82590342494a307c986457e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207397"
---
# <a name="icordebugprocessclearcurrentexception-method"></a><span data-ttu-id="7d71b-102">ICorDebugProcess::ClearCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="7d71b-102">ICorDebugProcess::ClearCurrentException Method</span></span>
<span data-ttu-id="7d71b-103">Vymaže aktuální nespravovanou výjimku na daném vlákně.</span><span class="sxs-lookup"><span data-stu-id="7d71b-103">Clears the current unmanaged exception on the given thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d71b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d71b-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d71b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d71b-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="7d71b-106">pro ID vlákna, na kterém bude vymazána aktuální nespravovanou výjimka.</span><span class="sxs-lookup"><span data-stu-id="7d71b-106">[in] The ID of the thread on which the current unmanaged exception will be cleared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d71b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d71b-107">Remarks</span></span>  
 <span data-ttu-id="7d71b-108">Před voláním metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) volejte tuto metodu, pokud vlákno oznámilo nespravovanou výjimku, kterou by měl ignorovat laděného procesu.</span><span class="sxs-lookup"><span data-stu-id="7d71b-108">Call this method before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) when a thread has reported an unmanaged exception that should be ignored by the debuggee.</span></span> <span data-ttu-id="7d71b-109">Tím se v daném vláknu vymažou nedokončené události v pásmu (IB) i mimo pásmo (OOB).</span><span class="sxs-lookup"><span data-stu-id="7d71b-109">This will clear both the outstanding in-band (IB) and out-of-band (OOB) events on the given thread.</span></span> <span data-ttu-id="7d71b-110">Všechny zarážky OOB a výjimky s jedním krokem se automaticky vymažou.</span><span class="sxs-lookup"><span data-stu-id="7d71b-110">All OOB breakpoints and single-step exceptions are automatically cleared.</span></span>  
  
 <span data-ttu-id="7d71b-111">K zachycení aktuální spravované výjimky ve vlákně použijte [ICorDebugThread2:: InterceptCurrentException –](icordebugthread2-interceptcurrentexception-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7d71b-111">Use [ICorDebugThread2::InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md) to intercept the current managed exception on a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d71b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d71b-112">Requirements</span></span>  
 <span data-ttu-id="7d71b-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d71b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d71b-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7d71b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d71b-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d71b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d71b-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d71b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
