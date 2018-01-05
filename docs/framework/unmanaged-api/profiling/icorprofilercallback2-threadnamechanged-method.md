---
title: "ICorProfilerCallback2::ThreadNameChanged – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.ThreadNameChanged
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ef0100111aa64aed2df7c63c332b54f026d1e26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="92f34-102">ICorProfilerCallback2::ThreadNameChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="92f34-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="92f34-103">Upozorní profileru kódu, že došlo ke změně názvu vlákna.</span><span class="sxs-lookup"><span data-stu-id="92f34-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92f34-104">Syntax</span></span>  
  
```  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92f34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92f34-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="92f34-106">[v] ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="92f34-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="92f34-107">[v] Délka názvu nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="92f34-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="92f34-108">[v] Název nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="92f34-108">[in] The new name of the thread.</span></span> <span data-ttu-id="92f34-109">Název není ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="92f34-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92f34-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92f34-110">Requirements</span></span>  
 <span data-ttu-id="92f34-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92f34-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92f34-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92f34-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92f34-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92f34-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92f34-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92f34-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f34-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="92f34-115">See Also</span></span>  
 [<span data-ttu-id="92f34-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92f34-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="92f34-117">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92f34-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
