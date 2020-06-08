---
title: ICorProfilerCallback::ClassUnloadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 14eb90c707618796d6d62ed2ec5710ceba31ba6c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500374"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="e448c-102">ICorProfilerCallback::ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="e448c-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="e448c-103">Upozorní profileru, že se dokončila uvolňování třídy.</span><span class="sxs-lookup"><span data-stu-id="e448c-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e448c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e448c-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e448c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e448c-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="e448c-106">\[v] identifikuje třídu, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="e448c-106">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="e448c-107">\[in] HRESULT, který označuje, zda byla třída úspěšně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="e448c-107">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="e448c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e448c-108">Remarks</span></span>  
 <span data-ttu-id="e448c-109">Některé části uvolňování třídy mohou pokračovat po `ClassUnloadFinished` zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="e448c-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="e448c-110">Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání.</span><span class="sxs-lookup"><span data-stu-id="e448c-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="e448c-111">Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část uvolňování třídy byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="e448c-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e448c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e448c-112">Requirements</span></span>  
 <span data-ttu-id="e448c-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e448c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e448c-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e448c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e448c-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e448c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e448c-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e448c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e448c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e448c-117">See also</span></span>

- [<span data-ttu-id="e448c-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e448c-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e448c-119">ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="e448c-119">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
