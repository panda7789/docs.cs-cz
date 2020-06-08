---
title: ICorProfilerCallback::AppDomainCreationStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: fcebe65b7f39dd2849946e445a694ad5e9b1a65d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500478"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="9964d-102">ICorProfilerCallback::AppDomainCreationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="9964d-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="9964d-103">Oznamuje profileru, že se vytváří doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="9964d-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9964d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9964d-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9964d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9964d-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="9964d-106">\[v] identifikuje doménu, která se vytváří.</span><span class="sxs-lookup"><span data-stu-id="9964d-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="9964d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9964d-107">Remarks</span></span>  
 <span data-ttu-id="9964d-108">IDENTIFIKÁTOR není platný pro žádné žádosti o informace, dokud není volána metoda [ICorProfilerCallback:: appdomaincreationfinished –](icorprofilercallback-appdomaincreationfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9964d-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9964d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9964d-109">Requirements</span></span>  
 <span data-ttu-id="9964d-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9964d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9964d-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9964d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9964d-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9964d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9964d-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9964d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9964d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9964d-114">See also</span></span>

- [<span data-ttu-id="9964d-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9964d-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
