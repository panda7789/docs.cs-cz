---
title: "ICorProfilerCallback::ModuleAttachedToAssembly – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6183014bf5487d0eebccf2fb70a13c363212046b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="929de-102">ICorProfilerCallback::ModuleAttachedToAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="929de-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="929de-103">Upozorní profileru, že se modul připojen k její nadřazené sestavení.</span><span class="sxs-lookup"><span data-stu-id="929de-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="929de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="929de-104">Syntax</span></span>  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="929de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="929de-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="929de-106">[v] ID modulu, který bude připojen.</span><span class="sxs-lookup"><span data-stu-id="929de-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="929de-107">[v] ID nadřazené sestavení, ke kterému je připojený modul.</span><span class="sxs-lookup"><span data-stu-id="929de-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="929de-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="929de-108">Remarks</span></span>  
 <span data-ttu-id="929de-109">Modul lze načíst prostřednictvím tabulku importních adres (IAT), prostřednictvím volání `LoadLibrary`, nebo prostřednictvím odkazu metadat.</span><span class="sxs-lookup"><span data-stu-id="929de-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="929de-110">V důsledku toho běžné zavaděč language runtime (CLR) má více cest kód pro určení sestavení, ve kterém je umístěn modul.</span><span class="sxs-lookup"><span data-stu-id="929de-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="929de-111">Proto je možné, že po [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) je volána, modul nebude vědět, jaké sestavení je v a získání ID nadřazeného sestavení není možné.</span><span class="sxs-lookup"><span data-stu-id="929de-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="929de-112">`ModuleAttachedToAssembly` Metoda je volána, když modul je připojen k její nadřazené sestavení a její nadřazené sestavení nelze získat ID.</span><span class="sxs-lookup"><span data-stu-id="929de-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="929de-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="929de-113">Requirements</span></span>  
 <span data-ttu-id="929de-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="929de-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="929de-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="929de-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="929de-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="929de-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="929de-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="929de-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="929de-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="929de-118">See Also</span></span>  
 [<span data-ttu-id="929de-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="929de-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
