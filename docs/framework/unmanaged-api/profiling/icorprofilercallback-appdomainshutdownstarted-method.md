---
title: "ICorProfilerCallback::AppDomainShutdownStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainShutdownStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 14e515ae13e0a445580dabcdfa30253da94fd216
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="ef0cf-102">ICorProfilerCallback::AppDomainShutdownStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="ef0cf-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="ef0cf-103">Upozorní profileru, že domény aplikace odpojení z procesu.</span><span class="sxs-lookup"><span data-stu-id="ef0cf-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef0cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef0cf-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef0cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef0cf-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="ef0cf-106">[v] Určuje doménu, ve kterém jsou uloženy sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef0cf-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef0cf-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef0cf-107">Remarks</span></span>  
 <span data-ttu-id="ef0cf-108">Hodnota `appDomainId` není platná pro všechny žádosti o informace po `AppDomainShutdownStarted` metoda vrátí – Toto je poslední možnost okna profilování a získat informace o této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef0cf-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef0cf-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef0cf-109">Requirements</span></span>  
 <span data-ttu-id="ef0cf-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef0cf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef0cf-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ef0cf-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef0cf-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef0cf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef0cf-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef0cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef0cf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef0cf-114">See Also</span></span>  
 [<span data-ttu-id="ef0cf-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ef0cf-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
