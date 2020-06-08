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
ms.openlocfilehash: 419195d9450bf07e5ad8c7cedcac76e175137c96
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498177"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="5b994-102">ICorProfilerInfo::GetHandleFromThread – metoda</span><span class="sxs-lookup"><span data-stu-id="5b994-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="5b994-103">Mapuje ID vlákna na popisovač vlákna Win32.</span><span class="sxs-lookup"><span data-stu-id="5b994-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b994-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b994-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b994-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b994-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="5b994-106">pro ID vlákna, které má být namapováno.</span><span class="sxs-lookup"><span data-stu-id="5b994-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="5b994-107">mimo Ukazatel na popisovač vlákna Win32.</span><span class="sxs-lookup"><span data-stu-id="5b994-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b994-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b994-108">Remarks</span></span>  
 <span data-ttu-id="5b994-109">Profiler musí `DuplicateHandle` před použitím volat funkci Win32 na popisovači.</span><span class="sxs-lookup"><span data-stu-id="5b994-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b994-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b994-110">Requirements</span></span>  
 <span data-ttu-id="5b994-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b994-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b994-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5b994-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b994-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5b994-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b994-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b994-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b994-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b994-115">See also</span></span>

- [<span data-ttu-id="5b994-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5b994-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
