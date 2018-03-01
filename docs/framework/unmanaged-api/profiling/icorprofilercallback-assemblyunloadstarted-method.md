---
title: "ICorProfilerCallback::AssemblyUnloadStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9984cff1d3c4013d66bc9eb7dbe5dbe7b61d2ba3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a><span data-ttu-id="ccfdb-102">ICorProfilerCallback::AssemblyUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="ccfdb-102">ICorProfilerCallback::AssemblyUnloadStarted Method</span></span>
<span data-ttu-id="ccfdb-103">Upozorní profileru odpojení sestavení.</span><span class="sxs-lookup"><span data-stu-id="ccfdb-103">Notifies the profiler that an assembly is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccfdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccfdb-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccfdb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccfdb-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="ccfdb-106">[v] Identifikuje sestavení, které odpojení.</span><span class="sxs-lookup"><span data-stu-id="ccfdb-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccfdb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccfdb-107">Remarks</span></span>  
 <span data-ttu-id="ccfdb-108">Hodnota `assemblyId` není platná pro požadavek informace po `AssemblyUnloadStarted` metoda vrátí – Toto je poslední možnost okna profilování a získat informace o tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="ccfdb-108">The value of `assemblyId` is not valid for an information request after the `AssemblyUnloadStarted` method returns — this is the profiler's last chance to get information about this assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccfdb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccfdb-109">Requirements</span></span>  
 <span data-ttu-id="ccfdb-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccfdb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccfdb-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ccfdb-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ccfdb-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccfdb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccfdb-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccfdb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccfdb-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccfdb-114">See Also</span></span>  
 [<span data-ttu-id="ccfdb-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccfdb-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ccfdb-116">AssemblyUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="ccfdb-116">AssemblyUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)
