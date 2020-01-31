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
ms.openlocfilehash: cb342b1c328daca5b3cfc0440e6f276ae54e3ed8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866179"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="910b9-102">ICorProfilerCallback::ModuleAttachedToAssembly – metoda</span><span class="sxs-lookup"><span data-stu-id="910b9-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="910b9-103">Upozorní profileru, že je modul připojen ke svému nadřazenému sestavení.</span><span class="sxs-lookup"><span data-stu-id="910b9-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="910b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="910b9-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="910b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="910b9-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="910b9-106">pro ID modulu, který se připojuje</span><span class="sxs-lookup"><span data-stu-id="910b9-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="910b9-107">pro ID nadřazeného sestavení, ke kterému je modul připojen</span><span class="sxs-lookup"><span data-stu-id="910b9-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="910b9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="910b9-108">Remarks</span></span>  
 <span data-ttu-id="910b9-109">Modul lze načíst prostřednictvím tabulky importních adres (IAT), prostřednictvím volání `LoadLibrary`nebo prostřednictvím odkazu na metadata.</span><span class="sxs-lookup"><span data-stu-id="910b9-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="910b9-110">V důsledku toho má zavaděč modulu CLR (Common Language Runtime) více cest kódu pro určení sestavení, ve kterém modul žije.</span><span class="sxs-lookup"><span data-stu-id="910b9-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="910b9-111">Proto je možné, že po volání metody [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) modul neví, v jakém sestavení je, a získat ID nadřazeného sestavení není možné.</span><span class="sxs-lookup"><span data-stu-id="910b9-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="910b9-112">Metoda `ModuleAttachedToAssembly` je volána, když je modul připojen ke svému nadřazenému sestavení a lze získat jeho nadřazené ID sestavení.</span><span class="sxs-lookup"><span data-stu-id="910b9-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="910b9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="910b9-113">Requirements</span></span>  
 <span data-ttu-id="910b9-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="910b9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="910b9-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="910b9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="910b9-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="910b9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="910b9-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="910b9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="910b9-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="910b9-118">See also</span></span>

- [<span data-ttu-id="910b9-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="910b9-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
