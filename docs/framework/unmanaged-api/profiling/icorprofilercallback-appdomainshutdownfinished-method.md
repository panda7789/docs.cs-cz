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
ms.openlocfilehash: 722a1e0adea41a13ca25829c53372c29187b80bd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500465"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="04653-102">ICorProfilerCallback::AppDomainShutdownFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="04653-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="04653-103">Upozorní profileru, že doména aplikace byla uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="04653-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04653-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04653-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04653-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04653-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="04653-106">\[v] identifikuje doménu, ve které jsou uložena sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="04653-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="04653-107">\[in] HRESULT, který označuje, zda byla doména aplikace úspěšně uvolněna.</span><span class="sxs-lookup"><span data-stu-id="04653-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="04653-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04653-108">Remarks</span></span>  
 <span data-ttu-id="04653-109">Hodnota `appDomainId` není platná pro požadavek na informace po návratu metody [ICorProfilerCallback:: appdomainshutdownstarted –](icorprofilercallback-appdomainshutdownstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="04653-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="04653-110">Některé části odložení aplikační domény můžou pokračovat i po `AppDomainCreationFinished` zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="04653-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="04653-111">Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání.</span><span class="sxs-lookup"><span data-stu-id="04653-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="04653-112">Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část uvolňování domény aplikace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="04653-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04653-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04653-113">Requirements</span></span>  
 <span data-ttu-id="04653-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04653-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04653-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="04653-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04653-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04653-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04653-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04653-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04653-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04653-118">See also</span></span>

- [<span data-ttu-id="04653-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04653-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
