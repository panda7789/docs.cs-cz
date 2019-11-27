---
title: ICorProfilerCallback::AppDomainShutdownFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: 8ff7d5a593388bd3a584e031aea411dfdb6c9845
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445194"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="2318d-102">ICorProfilerCallback::AppDomainShutdownFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="2318d-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="2318d-103">Upozorní profileru, že doména aplikace byla uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="2318d-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2318d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2318d-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2318d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2318d-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="2318d-106">pro Určuje doménu, ve které jsou uložena sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="2318d-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="2318d-107">pro Hodnota HRESULT, která označuje, zda byla doména aplikace úspěšně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="2318d-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2318d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2318d-108">Remarks</span></span>  
 <span data-ttu-id="2318d-109">Hodnota `appDomainId` není platná pro požadavek na informace po návratu metody [ICorProfilerCallback:: appdomainshutdownstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2318d-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="2318d-110">Některé části odinstalování domény aplikace můžou pokračovat i po `AppDomainCreationFinished` zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="2318d-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="2318d-111">Selhání HRESULT v `hrStatus` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="2318d-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="2318d-112">Úspěšnost HRESULT v `hrStatus` však znamená, že první část uvolňování domény aplikace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="2318d-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2318d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2318d-113">Requirements</span></span>  
 <span data-ttu-id="2318d-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2318d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2318d-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2318d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2318d-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2318d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2318d-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2318d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2318d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2318d-118">See also</span></span>

- [<span data-ttu-id="2318d-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2318d-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
