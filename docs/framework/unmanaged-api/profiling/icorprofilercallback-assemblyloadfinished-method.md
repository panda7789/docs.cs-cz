---
title: ICorProfilerCallback::AssemblyLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e32af790c755f65b5435455c326d011656da19ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198371"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="5c6ea-102">ICorProfilerCallback::AssemblyLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="5c6ea-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="5c6ea-103">Oznámí profileru, že sestavení bylo dokončeno načítání.</span><span class="sxs-lookup"><span data-stu-id="5c6ea-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c6ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c6ea-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c6ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c6ea-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="5c6ea-106">[in] Určuje sestavení, který byl načten.</span><span class="sxs-lookup"><span data-stu-id="5c6ea-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="5c6ea-107">[in] HRESULT, která určuje, zda sestavení bylo dokončeno načítání úspěšně.</span><span class="sxs-lookup"><span data-stu-id="5c6ea-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c6ea-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c6ea-108">Remarks</span></span>  
 <span data-ttu-id="5c6ea-109">Hodnota `assemblyId` není platná pro požadavek informace do `AssemblyLoadFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="5c6ea-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="5c6ea-110">Některé části načítání sestavení může pokračovat po `AssemblyLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="5c6ea-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="5c6ea-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="5c6ea-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="5c6ea-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část načítání sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="5c6ea-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c6ea-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c6ea-113">Requirements</span></span>  
 <span data-ttu-id="5c6ea-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c6ea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c6ea-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c6ea-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c6ea-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c6ea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c6ea-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c6ea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c6ea-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c6ea-118">See also</span></span>

- [<span data-ttu-id="5c6ea-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c6ea-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
