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
ms.openlocfilehash: 89f7ff2c213dc510268f9e6c802813a48e870d99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453844"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="4fe41-102">ICorProfilerInfo::GetCurrentThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="4fe41-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="4fe41-103">Získá ID aktuálního vlákna, pokud je spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="4fe41-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fe41-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4fe41-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4fe41-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="4fe41-106">[out] Ukazatel na vrácený ID spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="4fe41-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fe41-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fe41-107">Remarks</span></span>  
 <span data-ttu-id="4fe41-108">Pokud je aktuální vlákno zřetězení interní runtime nebo jiné vlákno nespravované `GetCurrentThreadID` vrátí CORPROF_E_NOT_MANAGED_THREAD jako hodnota HRESULT a vrácená hodnota `pThreadId` parametr bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4fe41-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fe41-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fe41-109">Requirements</span></span>  
 <span data-ttu-id="4fe41-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fe41-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fe41-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4fe41-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fe41-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fe41-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fe41-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fe41-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe41-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fe41-114">See Also</span></span>  
 [<span data-ttu-id="4fe41-115">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4fe41-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
