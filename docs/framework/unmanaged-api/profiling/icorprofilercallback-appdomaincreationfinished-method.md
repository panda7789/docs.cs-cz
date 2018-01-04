---
title: "ICorProfilerCallback::AppDomainCreationFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainCreationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f779e5a7b0b38558593e84c26b33784383765ca0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="8c671-102">ICorProfilerCallback::AppDomainCreationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="8c671-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="8c671-103">Upozorní profileru vytvořený domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="8c671-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c671-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c671-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c671-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c671-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="8c671-106">[v] Určuje doménu, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="8c671-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="8c671-107">[v] HRESULT, která určuje, zda vytváření domény aplikace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="8c671-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c671-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c671-108">Remarks</span></span>  
 <span data-ttu-id="8c671-109">ID aplikace není platný pro všechny informace požadavek, dokud `AppDomainCreationFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="8c671-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="8c671-110">Některé části načítání doménu aplikace, může pokračovat i po `AppDomainCreationFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="8c671-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="8c671-111">Selhání HRESULT v `hrStatus` znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="8c671-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="8c671-112">Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část vytváření domény aplikace byl úspěšný.</span><span class="sxs-lookup"><span data-stu-id="8c671-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c671-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8c671-113">Requirements</span></span>  
 <span data-ttu-id="8c671-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c671-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c671-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c671-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c671-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c671-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c671-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c671-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c671-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c671-118">See Also</span></span>  
 [<span data-ttu-id="8c671-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8c671-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
