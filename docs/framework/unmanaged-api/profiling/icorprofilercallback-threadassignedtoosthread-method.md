---
title: ICorProfilerCallback::ThreadAssignedToOSThread – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
ms.openlocfilehash: 182a82300183046ccb4a93a79af0dd8f23848c20
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503169"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="878b5-102">ICorProfilerCallback::ThreadAssignedToOSThread – metoda</span><span class="sxs-lookup"><span data-stu-id="878b5-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="878b5-103">Upozorní profileru, že spravované vlákno je implementováno pomocí konkrétního vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="878b5-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="878b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="878b5-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="878b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="878b5-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="878b5-106">pro Identifikátor spravovaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="878b5-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="878b5-107">pro Identifikátor vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="878b5-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="878b5-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="878b5-108">Remarks</span></span>  
 <span data-ttu-id="878b5-109">`ThreadAssignedToOSThread`Zpětné volání existuje, aby Profiler mohl udržovat přesné mapování mezi vlákny operačních systémů na spravovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="878b5-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="878b5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="878b5-110">Requirements</span></span>  
 <span data-ttu-id="878b5-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="878b5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="878b5-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="878b5-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="878b5-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="878b5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="878b5-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="878b5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878b5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="878b5-115">See also</span></span>

- [<span data-ttu-id="878b5-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="878b5-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
