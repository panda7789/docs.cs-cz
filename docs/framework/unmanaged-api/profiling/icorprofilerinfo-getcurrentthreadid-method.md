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
ms.openlocfilehash: fa0fe827300a86a906a254292434e2a56ebb4a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498398"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="668f6-102">ICorProfilerInfo::GetCurrentThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="668f6-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="668f6-103">Získá ID aktuálního vlákna, pokud se jedná o spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="668f6-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="668f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="668f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="668f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="668f6-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="668f6-106">mimo Ukazatel na vrácené ID spravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="668f6-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="668f6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="668f6-107">Remarks</span></span>  
 <span data-ttu-id="668f6-108">Pokud je aktuální vlákno interní běhové vlákno nebo jiné nespravované vlákno, `GetCurrentThreadID` vrátí CORPROF_E_NOT_MANAGED_THREAD jako HRESULT a vrácená hodnota `pThreadId` parametru bude null.</span><span class="sxs-lookup"><span data-stu-id="668f6-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="668f6-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="668f6-109">Requirements</span></span>  
 <span data-ttu-id="668f6-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="668f6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="668f6-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="668f6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="668f6-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="668f6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="668f6-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="668f6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="668f6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="668f6-114">See also</span></span>

- [<span data-ttu-id="668f6-115">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="668f6-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
