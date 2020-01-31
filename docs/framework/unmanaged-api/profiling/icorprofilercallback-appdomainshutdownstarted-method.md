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
ms.openlocfilehash: d280b008b34befce04159d02dfbb3de37b262c3c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866660"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="6cedf-102">ICorProfilerCallback::AppDomainShutdownStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="6cedf-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="6cedf-103">Upozorní profileru, že doména aplikace je uvolněna z procesu.</span><span class="sxs-lookup"><span data-stu-id="6cedf-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cedf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cedf-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cedf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cedf-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="6cedf-106">\[v] identifikuje doménu, ve které jsou uložena sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6cedf-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="6cedf-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cedf-107">Remarks</span></span>  
 <span data-ttu-id="6cedf-108">Hodnota `appDomainId` není platná pro žádnou žádost o informace po návratu metody `AppDomainShutdownStarted` – jedná se o poslední možnost profileru k získání informací o této doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="6cedf-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cedf-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cedf-109">Requirements</span></span>  
 <span data-ttu-id="6cedf-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cedf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cedf-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6cedf-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6cedf-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6cedf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cedf-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cedf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cedf-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cedf-114">See also</span></span>

- [<span data-ttu-id="6cedf-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cedf-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
