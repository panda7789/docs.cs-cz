---
title: ICorProfilerCallback2::ThreadNameChanged – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
ms.openlocfilehash: 1149298b4c5e521b37aae6ec48d463f395f18ae3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439567"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="c37c7-102">ICorProfilerCallback2::ThreadNameChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="c37c7-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="c37c7-103">Notifies the code profiler that the name of a thread has changed.</span><span class="sxs-lookup"><span data-stu-id="c37c7-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c37c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c37c7-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c37c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c37c7-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="c37c7-106">[in] The ID of the thread.</span><span class="sxs-lookup"><span data-stu-id="c37c7-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c37c7-107">[in] The length of the new name of the thread.</span><span class="sxs-lookup"><span data-stu-id="c37c7-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="c37c7-108">[in] The new name of the thread.</span><span class="sxs-lookup"><span data-stu-id="c37c7-108">[in] The new name of the thread.</span></span> <span data-ttu-id="c37c7-109">The name is not null-terminated.</span><span class="sxs-lookup"><span data-stu-id="c37c7-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c37c7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c37c7-110">Requirements</span></span>  
 <span data-ttu-id="c37c7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c37c7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c37c7-112">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c37c7-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c37c7-113">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c37c7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c37c7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c37c7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37c7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c37c7-115">See also</span></span>

- [<span data-ttu-id="c37c7-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c37c7-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c37c7-117">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c37c7-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
