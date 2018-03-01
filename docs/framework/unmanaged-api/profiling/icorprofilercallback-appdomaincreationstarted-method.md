---
title: "ICorProfilerCallback::AppDomainCreationStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe9089438f64bff19439af76c3f5eaf18fc5d6d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="d74b0-102">ICorProfilerCallback::AppDomainCreationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="d74b0-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="d74b0-103">Upozorní profileru se vytváří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="d74b0-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d74b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d74b0-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d74b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d74b0-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="d74b0-106">[v] Určuje doménu, která je právě vytvářena.</span><span class="sxs-lookup"><span data-stu-id="d74b0-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d74b0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d74b0-107">Remarks</span></span>  
 <span data-ttu-id="d74b0-108">Identifikátor není platné pro požadavek žádné informace, dokud [icorprofilercallback::appdomaincreationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="d74b0-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d74b0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d74b0-109">Requirements</span></span>  
 <span data-ttu-id="d74b0-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d74b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d74b0-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d74b0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d74b0-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d74b0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d74b0-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d74b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d74b0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d74b0-114">See Also</span></span>  
 [<span data-ttu-id="d74b0-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d74b0-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
