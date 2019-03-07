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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53bcc04c8d68a79217ebda5284efe7d8e18fdb91
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478775"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="b2785-102">ICorProfilerInfo::GetThreadInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="b2785-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="b2785-103">Získá aktuální identitu vlákna Win32 pro zadaný podproces.</span><span class="sxs-lookup"><span data-stu-id="b2785-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2785-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2785-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2785-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2785-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="b2785-106">[in] ID vlákna, pro které chcete získat aktuální ID Win32</span><span class="sxs-lookup"><span data-stu-id="b2785-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="b2785-107">[out] ID ukazatel na aktuální vlákno Win32 zadaného vlákna.</span><span class="sxs-lookup"><span data-stu-id="b2785-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2785-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2785-108">Requirements</span></span>  
 <span data-ttu-id="b2785-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2785-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2785-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2785-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2785-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2785-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2785-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2785-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2785-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2785-113">See also</span></span>
- [<span data-ttu-id="b2785-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2785-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
