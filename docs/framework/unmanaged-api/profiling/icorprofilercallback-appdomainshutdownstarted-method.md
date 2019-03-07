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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 174ac8b66c8127c16398de442a7067b742ab58ab
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465566"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="eaf74-102">ICorProfilerCallback::AppDomainShutdownStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="eaf74-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="eaf74-103">Oznámí profileru, že se z procesu uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaf74-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaf74-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaf74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eaf74-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="eaf74-106">[in] Určuje doménu, ve kterém jsou uložené sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaf74-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaf74-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eaf74-107">Remarks</span></span>  
 <span data-ttu-id="eaf74-108">Hodnota `appDomainId` není platná pro všechny žádosti o informace po `AppDomainShutdownStarted` metoda vrátí hodnotu – Toto je poslední možnost profileru a získat informace o této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="eaf74-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaf74-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eaf74-109">Requirements</span></span>  
 <span data-ttu-id="eaf74-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaf74-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaf74-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eaf74-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eaf74-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaf74-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaf74-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaf74-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf74-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaf74-114">See also</span></span>
- [<span data-ttu-id="eaf74-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eaf74-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
