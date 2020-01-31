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
ms.openlocfilehash: 038f922eaaeb7d660cfbdcc0facb89677bdd154e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863540"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="54eac-102">ICorProfilerInfo::GetHandleFromThread – metoda</span><span class="sxs-lookup"><span data-stu-id="54eac-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="54eac-103">Mapuje ID vlákna na popisovač vlákna Win32.</span><span class="sxs-lookup"><span data-stu-id="54eac-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54eac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54eac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54eac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54eac-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="54eac-106">pro ID vlákna, které má být namapováno.</span><span class="sxs-lookup"><span data-stu-id="54eac-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="54eac-107">mimo Ukazatel na popisovač vlákna Win32.</span><span class="sxs-lookup"><span data-stu-id="54eac-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54eac-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54eac-108">Remarks</span></span>  
 <span data-ttu-id="54eac-109">Profiler musí před použitím volat funkci Win32 `DuplicateHandle` na popisovači.</span><span class="sxs-lookup"><span data-stu-id="54eac-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54eac-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54eac-110">Requirements</span></span>  
 <span data-ttu-id="54eac-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54eac-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54eac-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="54eac-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54eac-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="54eac-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54eac-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54eac-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54eac-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54eac-115">See also</span></span>

- [<span data-ttu-id="54eac-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54eac-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
