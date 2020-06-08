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
ms.openlocfilehash: 45ae164e79f077549a1d685aa060484240546a10
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497943"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="47567-102">ICorProfilerInfo::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="47567-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="47567-103">Získá identitu kontextu aktuálně přidruženou k zadanému vláknu.</span><span class="sxs-lookup"><span data-stu-id="47567-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47567-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47567-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47567-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47567-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="47567-106">pro ID vlákna</span><span class="sxs-lookup"><span data-stu-id="47567-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="47567-107">mimo Ukazatel na ID kontextu aktuálně přidružené k zadanému vláknu.</span><span class="sxs-lookup"><span data-stu-id="47567-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="47567-108">Pokud k vláknu není momentálně přidružen žádný kontext, vrátí tato funkce CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="47567-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47567-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47567-109">Requirements</span></span>  
 <span data-ttu-id="47567-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47567-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47567-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="47567-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47567-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="47567-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47567-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47567-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47567-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47567-114">See also</span></span>

- [<span data-ttu-id="47567-115">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47567-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
