---
title: "ICorProfilerCallback::AssemblyLoadFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af5089603c2044b10061a32c5921b9eeadf86b36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="7b3a7-102">ICorProfilerCallback::AssemblyLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="7b3a7-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="7b3a7-103">Upozorní profileru, že sestavení dokončil načítání.</span><span class="sxs-lookup"><span data-stu-id="7b3a7-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b3a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b3a7-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b3a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b3a7-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="7b3a7-106">[v] Identifikuje sestavení, která byla načtena.</span><span class="sxs-lookup"><span data-stu-id="7b3a7-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7b3a7-107">[v] HRESULT, která určuje, zda je sestavení načítání dokončeno úspěšně.</span><span class="sxs-lookup"><span data-stu-id="7b3a7-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b3a7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b3a7-108">Remarks</span></span>  
 <span data-ttu-id="7b3a7-109">Hodnota `assemblyId` není platná pro požadavek informace, dokud `AssemblyLoadFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="7b3a7-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="7b3a7-110">Některé části načítání sestavení může pokračovat po `AssemblyLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7b3a7-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="7b3a7-111">Selhání HRESULT v `hrStatus` znamená chybu.</span><span class="sxs-lookup"><span data-stu-id="7b3a7-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="7b3a7-112">Ale úspěšné HRESULT v `hrStatus` pouze označuje, že první část načítání sestavení proběhl úspěšně.</span><span class="sxs-lookup"><span data-stu-id="7b3a7-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b3a7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b3a7-113">Requirements</span></span>  
 <span data-ttu-id="7b3a7-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b3a7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b3a7-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b3a7-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b3a7-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b3a7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b3a7-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b3a7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b3a7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b3a7-118">See Also</span></span>  
 [<span data-ttu-id="7b3a7-119">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b3a7-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
