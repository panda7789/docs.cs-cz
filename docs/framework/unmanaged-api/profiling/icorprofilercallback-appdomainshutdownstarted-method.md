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
ms.openlocfilehash: f422e99a5f6a4153368304ff0b33bbc55381575a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177109"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="4822c-102">ICorProfilerCallback::AppDomainShutdownStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="4822c-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="4822c-103">Oznámí profileru, že se z procesu uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="4822c-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4822c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4822c-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4822c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4822c-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="4822c-106">[in] Určuje doménu, ve kterém jsou uložené sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="4822c-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4822c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4822c-107">Remarks</span></span>  
 <span data-ttu-id="4822c-108">Hodnota `appDomainId` není platná pro všechny žádosti o informace po `AppDomainShutdownStarted` metoda vrátí hodnotu – Toto je poslední možnost profileru a získat informace o této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="4822c-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4822c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4822c-109">Requirements</span></span>  
 <span data-ttu-id="4822c-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4822c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4822c-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4822c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4822c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4822c-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4822c-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="4822c-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4822c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4822c-114">See also</span></span>

- [<span data-ttu-id="4822c-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4822c-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
