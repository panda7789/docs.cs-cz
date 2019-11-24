---
title: ICorProfilerCallback::AppDomainCreationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: eaf0ae2a1b86234495c1804cff8b74331b3e8021
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445272"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="1fef7-102">ICorProfilerCallback::AppDomainCreationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="1fef7-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="1fef7-103">Notifies the profiler that an application domain has been created.</span><span class="sxs-lookup"><span data-stu-id="1fef7-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fef7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fef7-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="1fef7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1fef7-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="1fef7-106">[in] Identifies the domain which has been created.</span><span class="sxs-lookup"><span data-stu-id="1fef7-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="1fef7-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span><span class="sxs-lookup"><span data-stu-id="1fef7-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fef7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fef7-108">Remarks</span></span>  
 <span data-ttu-id="1fef7-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span><span class="sxs-lookup"><span data-stu-id="1fef7-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="1fef7-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span><span class="sxs-lookup"><span data-stu-id="1fef7-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="1fef7-111">A failure HRESULT in `hrStatus` indicates a failure.</span><span class="sxs-lookup"><span data-stu-id="1fef7-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="1fef7-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span><span class="sxs-lookup"><span data-stu-id="1fef7-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fef7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1fef7-113">Requirements</span></span>  
 <span data-ttu-id="1fef7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fef7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fef7-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1fef7-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1fef7-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fef7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fef7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fef7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fef7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fef7-118">See also</span></span>

- [<span data-ttu-id="1fef7-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1fef7-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
