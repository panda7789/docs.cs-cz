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
ms.openlocfilehash: db5ed871734205d59c602cc8b5c0cc9e8ac4682a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762868"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="a817a-102">ICorProfilerInfo::GetCurrentThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="a817a-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="a817a-103">Získá ID aktuálního vlákna, pokud je spravovaným vláknem.</span><span class="sxs-lookup"><span data-stu-id="a817a-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a817a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a817a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a817a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a817a-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="a817a-106">[out] Ukazatel na vrácené ID spravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="a817a-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a817a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a817a-107">Remarks</span></span>  
 <span data-ttu-id="a817a-108">Pokud je aktuální vlákno zřetězení vnitřního modulu runtime nebo jiných nespravovaného vlákna `GetCurrentThreadID` vrátí CORPROF_E_NOT_MANAGED_THREAD jako hodnota HRESULT a vrácená hodnota `pThreadId` parametr bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="a817a-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a817a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a817a-109">Requirements</span></span>  
 <span data-ttu-id="a817a-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a817a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a817a-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a817a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a817a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a817a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a817a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a817a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a817a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a817a-114">See also</span></span>

- [<span data-ttu-id="a817a-115">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a817a-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
