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
ms.openlocfilehash: 8b3f7712436c001e5cd44f214f6edb06390abd41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177069"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="f2516-102">ICorProfilerCallback::AppDomainCreationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="f2516-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="f2516-103">Upozorní profiler, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2516-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2516-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2516-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="f2516-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2516-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="f2516-106">\[in] Identifikuje doménu, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="f2516-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="f2516-107">\[in] HRESULT, který označuje, zda bylo vytvoření domény aplikace úspěšně dokončeno.</span><span class="sxs-lookup"><span data-stu-id="f2516-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="f2516-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2516-108">Remarks</span></span>  
 <span data-ttu-id="f2516-109">ID aplikace není platné pro žádný `AppDomainCreationFinished` požadavek na informace, dokud není metoda volána.</span><span class="sxs-lookup"><span data-stu-id="f2516-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="f2516-110">Některé části načítání domény aplikace může `AppDomainCreationFinished` pokračovat po zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="f2516-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="f2516-111">Selhání HRESULT `hrStatus` in označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="f2516-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f2516-112">Úspěch HRESULT v `hrStatus` šak v však označuje pouze, že první část vytvoření domény aplikace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f2516-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2516-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2516-113">Requirements</span></span>  
 <span data-ttu-id="f2516-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2516-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2516-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2516-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2516-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2516-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2516-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2516-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2516-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2516-118">See also</span></span>

- [<span data-ttu-id="f2516-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2516-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
