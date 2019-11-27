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
ms.openlocfilehash: 6a0f6dc9d2559bafed416d409063088d2f51c27d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445215"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="c43d0-102">ICorProfilerCallback::AppDomainCreationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="c43d0-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="c43d0-103">Oznamuje profileru, že se vytváří doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="c43d0-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c43d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c43d0-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c43d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c43d0-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="c43d0-106">pro Určuje doménu, která se vytváří.</span><span class="sxs-lookup"><span data-stu-id="c43d0-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c43d0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c43d0-107">Remarks</span></span>  
 <span data-ttu-id="c43d0-108">IDENTIFIKÁTOR není platný pro žádné žádosti o informace, dokud není volána metoda [ICorProfilerCallback:: appdomaincreationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c43d0-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c43d0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c43d0-109">Requirements</span></span>  
 <span data-ttu-id="c43d0-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c43d0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c43d0-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c43d0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c43d0-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c43d0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c43d0-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c43d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c43d0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c43d0-114">See also</span></span>

- [<span data-ttu-id="c43d0-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c43d0-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
