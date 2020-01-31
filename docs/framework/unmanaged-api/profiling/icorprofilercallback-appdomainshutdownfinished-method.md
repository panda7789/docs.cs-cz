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
ms.openlocfilehash: 0851ac33a2bac4fcf727cf09e5225f6b83481b50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866673"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="33086-102">ICorProfilerCallback::AppDomainShutdownFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="33086-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="33086-103">Upozorní profileru, že doména aplikace byla uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="33086-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33086-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33086-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33086-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33086-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="33086-106">\[v] identifikuje doménu, ve které jsou uložena sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="33086-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="33086-107">\[in] hodnota HRESULT, která označuje, zda byla doména aplikace úspěšně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="33086-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="33086-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33086-108">Remarks</span></span>  
 <span data-ttu-id="33086-109">Hodnota `appDomainId` není platná pro požadavek na informace po návratu metody [ICorProfilerCallback:: appdomainshutdownstarted –](icorprofilercallback-appdomainshutdownstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33086-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="33086-110">Některé části odinstalování domény aplikace můžou pokračovat i po `AppDomainCreationFinished` zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="33086-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="33086-111">Selhání HRESULT v `hrStatus` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="33086-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="33086-112">Úspěšnost HRESULT v `hrStatus` však znamená, že první část uvolňování domény aplikace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="33086-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33086-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33086-113">Requirements</span></span>  
 <span data-ttu-id="33086-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33086-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33086-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="33086-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33086-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="33086-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33086-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33086-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33086-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33086-118">See also</span></span>

- [<span data-ttu-id="33086-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33086-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
