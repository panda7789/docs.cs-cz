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
ms.openlocfilehash: 1b8afe10563d61e3ddab93e8d1b57eee4b6765c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766842"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="6d083-102">ICorProfilerInfo::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="6d083-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="6d083-103">Získá kontext identity aktuálně přiřazen k zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="6d083-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d083-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d083-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d083-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d083-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="6d083-106">[in] ID vlákna.</span><span class="sxs-lookup"><span data-stu-id="6d083-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="6d083-107">[out] Ukazatel na ID kontextu, který je aktuálně přiřazen k zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="6d083-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="6d083-108">Pokud vlákno nemá žádný kontext aktuálně přidružen, tato funkce vrátí CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="6d083-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d083-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d083-109">Requirements</span></span>  
 <span data-ttu-id="6d083-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d083-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d083-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d083-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d083-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d083-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d083-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d083-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d083-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d083-114">See also</span></span>

- [<span data-ttu-id="6d083-115">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d083-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
