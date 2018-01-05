---
title: "ICorProfilerCallback::AppDomainShutdownFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainShutdownFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e681c64017e99eaaf0b786e48ca96b4435b08890
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="0b692-102">ICorProfilerCallback::AppDomainShutdownFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="0b692-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="0b692-103">Upozorní profileru, že domény aplikace byl odpojen z procesu.</span><span class="sxs-lookup"><span data-stu-id="0b692-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b692-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b692-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b692-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b692-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="0b692-106">[v] Určuje doménu, ve kterém jsou uloženy sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="0b692-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="0b692-107">[v] HRESULT, která určuje, zda byla domény aplikace úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="0b692-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b692-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b692-108">Remarks</span></span>  
 <span data-ttu-id="0b692-109">Hodnota `appDomainId` není platná pro požadavek informace po [icorprofilercallback::appdomainshutdownstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="0b692-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="0b692-110">Některé části uvolnění domény aplikace, může pokračovat i po `AppDomainCreationFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="0b692-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="0b692-111">Selhání HRESULT v `hrStatus` znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="0b692-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="0b692-112">Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část uvolnění domény aplikace byl úspěšný.</span><span class="sxs-lookup"><span data-stu-id="0b692-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b692-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b692-113">Requirements</span></span>  
 <span data-ttu-id="0b692-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b692-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b692-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0b692-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b692-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b692-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b692-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b692-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b692-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b692-118">See Also</span></span>  
 [<span data-ttu-id="0b692-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b692-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
