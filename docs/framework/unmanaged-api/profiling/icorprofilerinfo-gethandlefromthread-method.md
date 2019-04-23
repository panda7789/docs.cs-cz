---
title: ICorProfilerInfo::GetHandleFromThread – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fc26ad9b25ad243bf868d6ef3155360509e6483
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185741"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="ade82-102">ICorProfilerInfo::GetHandleFromThread – metoda</span><span class="sxs-lookup"><span data-stu-id="ade82-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="ade82-103">Mapuje ID vlákna na popisovač podprocesu Win32.</span><span class="sxs-lookup"><span data-stu-id="ade82-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ade82-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ade82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ade82-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ade82-106">[in] ID vlákna, která má být mapována.</span><span class="sxs-lookup"><span data-stu-id="ade82-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="ade82-107">[out] Ukazatel na popisovač podprocesu Win32.</span><span class="sxs-lookup"><span data-stu-id="ade82-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ade82-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ade82-108">Remarks</span></span>  
 <span data-ttu-id="ade82-109">Profiler musí volat Win32 `DuplicateHandle` funkce na popisovač před jeho použitím.</span><span class="sxs-lookup"><span data-stu-id="ade82-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ade82-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ade82-110">Requirements</span></span>  
 <span data-ttu-id="ade82-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ade82-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade82-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ade82-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ade82-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ade82-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ade82-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade82-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade82-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ade82-115">See also</span></span>

- [<span data-ttu-id="ade82-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ade82-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
