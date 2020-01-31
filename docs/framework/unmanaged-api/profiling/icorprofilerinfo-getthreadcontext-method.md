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
ms.openlocfilehash: f8eff85392d355ea54980ac6b29e3c4cebb1b240
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869592"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="00e56-102">ICorProfilerInfo::GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="00e56-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="00e56-103">Získá identitu kontextu aktuálně přidruženou k zadanému vláknu.</span><span class="sxs-lookup"><span data-stu-id="00e56-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00e56-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00e56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00e56-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="00e56-106">pro ID vlákna</span><span class="sxs-lookup"><span data-stu-id="00e56-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="00e56-107">mimo Ukazatel na ID kontextu aktuálně přidružené k zadanému vláknu.</span><span class="sxs-lookup"><span data-stu-id="00e56-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="00e56-108">Pokud k vláknu není momentálně přidružen žádný kontext, vrátí tato funkce CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="00e56-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00e56-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00e56-109">Requirements</span></span>  
 <span data-ttu-id="00e56-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00e56-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00e56-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="00e56-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00e56-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="00e56-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00e56-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00e56-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e56-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00e56-114">See also</span></span>

- [<span data-ttu-id="00e56-115">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00e56-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
