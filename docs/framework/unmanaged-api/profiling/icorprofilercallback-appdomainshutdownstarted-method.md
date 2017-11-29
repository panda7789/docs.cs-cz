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
ms.openlocfilehash: 5eff8807b5f50708b8d8e4935052de89f59eb5d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="dda6a-102">ICorProfilerCallback::AppDomainShutdownStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="dda6a-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="dda6a-103">Upozorní profileru, že domény aplikace odpojení z procesu.</span><span class="sxs-lookup"><span data-stu-id="dda6a-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dda6a-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dda6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dda6a-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="dda6a-106">[v] Určuje doménu, ve kterém jsou uloženy sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="dda6a-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dda6a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dda6a-107">Remarks</span></span>  
 <span data-ttu-id="dda6a-108">Hodnota `appDomainId` není platná pro všechny žádosti o informace po `AppDomainShutdownStarted` metoda vrátí – Toto je poslední možnost okna profilování a získat informace o této domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="dda6a-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda6a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dda6a-109">Requirements</span></span>  
 <span data-ttu-id="dda6a-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dda6a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dda6a-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dda6a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dda6a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dda6a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dda6a-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dda6a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda6a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="dda6a-114">See Also</span></span>  
 [<span data-ttu-id="dda6a-115">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dda6a-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
