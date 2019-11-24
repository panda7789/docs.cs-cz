---
title: ICorProfilerCallback::AppDomainShutdownStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: 6bbb41f8fd3ac37f1c21fe8b4f6159e3d303777c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445192"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="ac33c-102">ICorProfilerCallback::AppDomainShutdownStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="ac33c-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="ac33c-103">Notifies the profiler that an application domain is being unloaded from a process.</span><span class="sxs-lookup"><span data-stu-id="ac33c-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac33c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac33c-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac33c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac33c-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="ac33c-106">[in] Identifies the domain in which the application's assemblies are stored.</span><span class="sxs-lookup"><span data-stu-id="ac33c-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac33c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac33c-107">Remarks</span></span>  
 <span data-ttu-id="ac33c-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span><span class="sxs-lookup"><span data-stu-id="ac33c-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac33c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ac33c-109">Requirements</span></span>  
 <span data-ttu-id="ac33c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac33c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac33c-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac33c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac33c-112">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac33c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac33c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac33c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac33c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac33c-114">See also</span></span>

- [<span data-ttu-id="ac33c-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ac33c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
