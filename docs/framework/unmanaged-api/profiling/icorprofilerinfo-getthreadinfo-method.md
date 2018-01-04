---
title: "ICorProfilerInfo::GetThreadInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetThreadInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ab887cf4aaded260903cf1b91498c7641eeb0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="5238e-102">ICorProfilerInfo::GetThreadInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="5238e-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="5238e-103">Získá aktuální vlákno identitu Win32 pro zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="5238e-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5238e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5238e-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5238e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5238e-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="5238e-106">[v] ID vlákna, pro které chcete získat aktuální ID Win32</span><span class="sxs-lookup"><span data-stu-id="5238e-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="5238e-107">[out] ID ukazatel na aktuální vlákno Win32 zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="5238e-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5238e-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5238e-108">Requirements</span></span>  
 <span data-ttu-id="5238e-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5238e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5238e-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5238e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5238e-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5238e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5238e-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5238e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5238e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5238e-113">See Also</span></span>  
 [<span data-ttu-id="5238e-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5238e-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
