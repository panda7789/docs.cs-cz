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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98fac8630403107f96f2fa86e5bcc9b0e60d0d08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737160"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="352f5-102">ICorProfilerCallback::AppDomainCreationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="352f5-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="352f5-103">Oznámí profileru, že se vytváří domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="352f5-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="352f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="352f5-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="352f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="352f5-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="352f5-106">[in] Určuje doménu, který se vytváří.</span><span class="sxs-lookup"><span data-stu-id="352f5-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="352f5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="352f5-107">Remarks</span></span>  
 <span data-ttu-id="352f5-108">Identifikátor není platný pro všechny žádost o informace, dokud [icorprofilercallback::appdomaincreationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="352f5-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="352f5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="352f5-109">Requirements</span></span>  
 <span data-ttu-id="352f5-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="352f5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="352f5-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="352f5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="352f5-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="352f5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="352f5-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="352f5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="352f5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="352f5-114">See also</span></span>
- [<span data-ttu-id="352f5-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="352f5-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
