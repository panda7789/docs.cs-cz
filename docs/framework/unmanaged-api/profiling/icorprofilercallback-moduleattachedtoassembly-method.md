---
title: ICorProfilerCallback::ModuleAttachedToAssembly – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3345e2e87ba41f750031deed2d15e13dbe4f06c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769279"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="eb74a-102">ICorProfilerCallback::ModuleAttachedToAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="eb74a-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="eb74a-103">Oznámí profileru, že se modul připojen k její nadřazené sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb74a-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb74a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb74a-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb74a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb74a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="eb74a-106">[in] ID modulu, který bude připojen.</span><span class="sxs-lookup"><span data-stu-id="eb74a-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="eb74a-107">[in] ID nadřazené sestavení, ke kterému je připojený modul.</span><span class="sxs-lookup"><span data-stu-id="eb74a-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb74a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb74a-108">Remarks</span></span>  
 <span data-ttu-id="eb74a-109">Modul lze načíst prostřednictvím tabulka importních adres (IAT), pomocí volání `LoadLibrary`, nebo přes odkaz na metadata.</span><span class="sxs-lookup"><span data-stu-id="eb74a-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="eb74a-110">V důsledku toho běžné zavaděč jazyka runtime (CLR) má více cest kódu pro určení sestavení, ve kterém se modul nachází.</span><span class="sxs-lookup"><span data-stu-id="eb74a-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="eb74a-111">Proto je možné, že po [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) nazývá modul neví, jaké sestavení je v a získání ID nadřazeného sestavení není možné.</span><span class="sxs-lookup"><span data-stu-id="eb74a-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="eb74a-112">`ModuleAttachedToAssembly` Metoda se volá, když modul je připojena k její nadřazené sestavení a jeho nadřazené sestavení můžete získat ID.</span><span class="sxs-lookup"><span data-stu-id="eb74a-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb74a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb74a-113">Requirements</span></span>  
 <span data-ttu-id="eb74a-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb74a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb74a-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb74a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb74a-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb74a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb74a-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb74a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb74a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb74a-118">See also</span></span>

- [<span data-ttu-id="eb74a-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb74a-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
