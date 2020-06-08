---
title: ICorProfilerInfo::GetThreadInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
ms.openlocfilehash: 532288364b2db1e6be49b9e6f87019b1e41e6866
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497917"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="43462-102">ICorProfilerInfo::GetThreadInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="43462-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="43462-103">Získá aktuální identitu vlákna Win32 pro zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="43462-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43462-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43462-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43462-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43462-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="43462-106">pro ID vlákna, pro které se má získat aktuální ID Win32</span><span class="sxs-lookup"><span data-stu-id="43462-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="43462-107">mimo Ukazatel na aktuální ID vlákna Win32 daného vlákna.</span><span class="sxs-lookup"><span data-stu-id="43462-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43462-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43462-108">Requirements</span></span>  
 <span data-ttu-id="43462-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43462-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43462-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="43462-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43462-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="43462-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43462-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43462-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43462-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43462-113">See also</span></span>

- [<span data-ttu-id="43462-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43462-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
