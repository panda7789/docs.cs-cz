---
title: ICorProfilerInfo2::GetThreadAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
ms.openlocfilehash: 7c1ee1c39fbf2dcc1f16df3bc94a235676a216dd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862565"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="c6e14-102">ICorProfilerInfo2::GetThreadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="c6e14-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="c6e14-103">Získá ID domény aplikace, ve které zadané vlákno aktuálně spouští kód.</span><span class="sxs-lookup"><span data-stu-id="c6e14-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6e14-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6e14-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6e14-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="c6e14-106">pro ID určující vlákno.</span><span class="sxs-lookup"><span data-stu-id="c6e14-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="c6e14-107">mimo Ukazatel na ID domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6e14-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6e14-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6e14-108">Requirements</span></span>  
 <span data-ttu-id="c6e14-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6e14-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6e14-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c6e14-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6e14-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c6e14-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6e14-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6e14-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e14-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6e14-113">See also</span></span>

- [<span data-ttu-id="c6e14-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6e14-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="c6e14-115">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6e14-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
