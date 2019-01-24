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
ms.openlocfilehash: f76a3cb232042ba6b91046d1f7b6e1d46ad6faef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634854"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="cd23d-102">ICorProfilerCallback::AssemblyLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="cd23d-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="cd23d-103">Oznámí profileru, že sestavení bylo dokončeno načítání.</span><span class="sxs-lookup"><span data-stu-id="cd23d-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd23d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd23d-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd23d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd23d-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="cd23d-106">[in] Určuje sestavení, který byl načten.</span><span class="sxs-lookup"><span data-stu-id="cd23d-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="cd23d-107">[in] HRESULT, která určuje, zda sestavení bylo dokončeno načítání úspěšně.</span><span class="sxs-lookup"><span data-stu-id="cd23d-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd23d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd23d-108">Remarks</span></span>  
 <span data-ttu-id="cd23d-109">Hodnota `assemblyId` není platná pro požadavek informace do `AssemblyLoadFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="cd23d-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="cd23d-110">Některé části načítání sestavení může pokračovat po `AssemblyLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="cd23d-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="cd23d-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="cd23d-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="cd23d-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část načítání sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="cd23d-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd23d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd23d-113">Requirements</span></span>  
 <span data-ttu-id="cd23d-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd23d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd23d-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd23d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd23d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd23d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd23d-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd23d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd23d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd23d-118">See also</span></span>
- [<span data-ttu-id="cd23d-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd23d-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
