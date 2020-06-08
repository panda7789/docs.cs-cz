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
ms.openlocfilehash: 1b973cdeaffbec0dad1f2d082c44e8001647fdcc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500452"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="13c07-102">ICorProfilerCallback::AppDomainShutdownStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="13c07-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="13c07-103">Upozorní profileru, že doména aplikace je uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="13c07-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13c07-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13c07-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13c07-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="13c07-106">\[v] identifikuje doménu, ve které jsou uložena sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="13c07-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="13c07-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13c07-107">Remarks</span></span>  
 <span data-ttu-id="13c07-108">Hodnota `appDomainId` není platná pro žádnou žádost o informace po `AppDomainShutdownStarted` návratu metody – jedná se o poslední možnost profileru k získání informací o této doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="13c07-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c07-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13c07-109">Requirements</span></span>  
 <span data-ttu-id="13c07-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c07-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c07-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="13c07-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13c07-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="13c07-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13c07-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c07-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c07-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13c07-114">See also</span></span>

- [<span data-ttu-id="13c07-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13c07-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
