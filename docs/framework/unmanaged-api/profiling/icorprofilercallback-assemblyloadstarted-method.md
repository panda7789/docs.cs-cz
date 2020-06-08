---
title: ICorProfilerCallback::AssemblyLoadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: df172edb97a82ae3bf2d46c8be6ea05d5445a09a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500426"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="8d8c7-102">ICorProfilerCallback::AssemblyLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="8d8c7-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="8d8c7-103">Upozorní profileru, že je načteno sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d8c7-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d8c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d8c7-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d8c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d8c7-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="8d8c7-106">\[v] identifikuje sestavení, které je načítáno.</span><span class="sxs-lookup"><span data-stu-id="8d8c7-106">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d8c7-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d8c7-107">Remarks</span></span>  
 <span data-ttu-id="8d8c7-108">Hodnota `assemblyId` není platná pro požadavek na informace, dokud není volána metoda [ICorProfilerCallback:: assemblyloadfinished –](icorprofilercallback-assemblyloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8d8c7-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d8c7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d8c7-109">Requirements</span></span>  
 <span data-ttu-id="8d8c7-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d8c7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d8c7-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8d8c7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d8c7-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8d8c7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d8c7-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d8c7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8c7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d8c7-114">See also</span></span>

- [<span data-ttu-id="8d8c7-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d8c7-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
