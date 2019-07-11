---
title: ICorProfilerCallback::ModuleLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c04b7862363b441ab35d6dd364c4dffaf7464153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769225"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="01215-102">ICorProfilerCallback::ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="01215-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="01215-103">Upozorní profiler modulu dokončení načítání.</span><span class="sxs-lookup"><span data-stu-id="01215-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01215-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01215-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01215-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01215-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="01215-106">[in] ID modulu, který se dokončila načítání.</span><span class="sxs-lookup"><span data-stu-id="01215-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="01215-107">[in] HRESULT, která určuje, jestli byl modul načten úspěšně.</span><span class="sxs-lookup"><span data-stu-id="01215-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01215-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01215-108">Remarks</span></span>  
 <span data-ttu-id="01215-109">Hodnota `moduleId` není platná pro požadavek informace do `ModuleLoadFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="01215-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="01215-110">Některé části načítání modulu může pokračovat po `ModuleLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="01215-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="01215-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="01215-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="01215-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že má první část načítání modulu bylo úspěšné.</span><span class="sxs-lookup"><span data-stu-id="01215-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01215-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01215-113">Requirements</span></span>  
 <span data-ttu-id="01215-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01215-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01215-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01215-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01215-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01215-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01215-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01215-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01215-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01215-118">See also</span></span>

- [<span data-ttu-id="01215-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01215-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="01215-120">ModuleLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="01215-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
