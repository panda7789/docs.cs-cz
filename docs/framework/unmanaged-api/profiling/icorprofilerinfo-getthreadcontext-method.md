---
title: ICorProfilerInfo::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb686be625d0d38bcf0de496c192276ebaa3410d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629566"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="5566a-102">ICorProfilerInfo::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="5566a-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="5566a-103">Získá kontext identity aktuálně přiřazen k zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="5566a-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5566a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5566a-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5566a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5566a-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="5566a-106">[in] ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="5566a-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="5566a-107">[out] Ukazatel na ID kontextu, který je aktuálně přiřazen k zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="5566a-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="5566a-108">Pokud vlákno nemá žádný kontext aktuálně přidružen, tato funkce vrátí CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="5566a-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5566a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5566a-109">Requirements</span></span>  
 <span data-ttu-id="5566a-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5566a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5566a-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5566a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5566a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5566a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5566a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5566a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5566a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5566a-114">See also</span></span>
- [<span data-ttu-id="5566a-115">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5566a-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
