---
title: "ICorProfilerCallback::ClassLoadFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae55325f514f9bec3efdf4764958e4b3fafd922b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="3c5f7-102">ICorProfilerCallback::ClassLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="3c5f7-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="3c5f7-103">Upozorní profileru, že třídu dokončil načítání.</span><span class="sxs-lookup"><span data-stu-id="3c5f7-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c5f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c5f7-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c5f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c5f7-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="3c5f7-106">[v] Určuje třídu, která byla načtena.</span><span class="sxs-lookup"><span data-stu-id="3c5f7-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="3c5f7-107">[v] HRESULT, která určuje, zda třída úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="3c5f7-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c5f7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c5f7-108">Remarks</span></span>  
 <span data-ttu-id="3c5f7-109">Hodnota `classId` není platná pro požadavek informace, dokud `ClassLoadFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="3c5f7-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="3c5f7-110">Některé části načítání třída může pokračovat po `ClassLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="3c5f7-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="3c5f7-111">Selhání HRESULT v `hrStatus` znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="3c5f7-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="3c5f7-112">Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část načítání třída proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="3c5f7-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c5f7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c5f7-113">Requirements</span></span>  
 <span data-ttu-id="3c5f7-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c5f7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c5f7-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c5f7-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3c5f7-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c5f7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c5f7-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c5f7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5f7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c5f7-118">See Also</span></span>  
 [<span data-ttu-id="3c5f7-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c5f7-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3c5f7-120">ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="3c5f7-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
