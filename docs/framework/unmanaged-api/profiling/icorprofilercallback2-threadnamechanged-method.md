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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd350c843c32102291de8327f5c37b27e287fd5c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706362"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="7b5e4-102">ICorProfilerCallback2::ThreadNameChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="7b5e4-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="7b5e4-103">Upozornění profileru kód, název vlákna se změnila.</span><span class="sxs-lookup"><span data-stu-id="7b5e4-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b5e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b5e4-104">Syntax</span></span>  
  
```  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b5e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b5e4-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="7b5e4-106">[in] ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="7b5e4-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7b5e4-107">[in] Délka názvu nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="7b5e4-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="7b5e4-108">[in] Nový název vlákna.</span><span class="sxs-lookup"><span data-stu-id="7b5e4-108">[in] The new name of the thread.</span></span> <span data-ttu-id="7b5e4-109">Název není ukončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="7b5e4-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b5e4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b5e4-110">Requirements</span></span>  
 <span data-ttu-id="7b5e4-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b5e4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b5e4-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b5e4-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b5e4-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b5e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b5e4-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b5e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b5e4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b5e4-115">See also</span></span>
- [<span data-ttu-id="7b5e4-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b5e4-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7b5e4-117">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b5e4-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
