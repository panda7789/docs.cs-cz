---
title: ICorProfilerInfo::GetCurrentThreadID – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 802072f3a0151aabc5ca5796df57ea7c694a2070
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041207"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="380a6-102">ICorProfilerInfo::GetCurrentThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="380a6-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="380a6-103">Získá ID aktuálního vlákna, pokud je spravovaným vláknem.</span><span class="sxs-lookup"><span data-stu-id="380a6-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="380a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="380a6-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="380a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="380a6-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="380a6-106">[out] Ukazatel na vrácené ID spravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="380a6-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="380a6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="380a6-107">Remarks</span></span>  
 <span data-ttu-id="380a6-108">Pokud je aktuální vlákno zřetězení vnitřního modulu runtime nebo jiných nespravovaného vlákna `GetCurrentThreadID` vrátí CORPROF_E_NOT_MANAGED_THREAD jako hodnota HRESULT a vrácená hodnota `pThreadId` parametr bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="380a6-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="380a6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="380a6-109">Requirements</span></span>  
 <span data-ttu-id="380a6-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="380a6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="380a6-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="380a6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="380a6-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="380a6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="380a6-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="380a6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="380a6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="380a6-114">See also</span></span>

- [<span data-ttu-id="380a6-115">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="380a6-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
