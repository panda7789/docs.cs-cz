---
title: ICorProfilerCallback::ClassUnloadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 86402abca5386f34256f1f44f674f1e1898ad5fd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500348"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="97e69-102">ICorProfilerCallback::ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="97e69-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="97e69-103">Upozorní profileru, že je uvolněna třída.</span><span class="sxs-lookup"><span data-stu-id="97e69-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97e69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97e69-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97e69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97e69-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="97e69-106">\[v] identifikuje třídu, která je uvolněna.</span><span class="sxs-lookup"><span data-stu-id="97e69-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="97e69-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97e69-107">Remarks</span></span>  
 <span data-ttu-id="97e69-108">Hodnota `classId` není platná pro požadavek na informace, poté co `ClassUnloadStarted` Metoda vrátí hodnotu – jedná se o poslední možnost profileru k získání informací o této třídě.</span><span class="sxs-lookup"><span data-stu-id="97e69-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97e69-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97e69-109">Requirements</span></span>  
 <span data-ttu-id="97e69-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97e69-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97e69-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="97e69-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97e69-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="97e69-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97e69-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97e69-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97e69-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97e69-114">See also</span></span>

- [<span data-ttu-id="97e69-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97e69-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="97e69-116">ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="97e69-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
