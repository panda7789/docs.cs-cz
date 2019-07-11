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
ms.openlocfilehash: 174e71fca8c59dbd4842d0fc0b84bb9a3d7b10df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763040"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="a915c-102">ICorProfilerCallback::AssemblyLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="a915c-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="a915c-103">Oznámí profileru, že sestavení bylo dokončeno načítání.</span><span class="sxs-lookup"><span data-stu-id="a915c-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a915c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a915c-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a915c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a915c-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="a915c-106">[in] Určuje sestavení, který byl načten.</span><span class="sxs-lookup"><span data-stu-id="a915c-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="a915c-107">[in] HRESULT, která určuje, zda sestavení bylo dokončeno načítání úspěšně.</span><span class="sxs-lookup"><span data-stu-id="a915c-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a915c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a915c-108">Remarks</span></span>  
 <span data-ttu-id="a915c-109">Hodnota `assemblyId` není platná pro požadavek informace do `AssemblyLoadFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="a915c-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="a915c-110">Některé části načítání sestavení může pokračovat po `AssemblyLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a915c-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="a915c-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="a915c-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="a915c-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část načítání sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="a915c-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a915c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a915c-113">Requirements</span></span>  
 <span data-ttu-id="a915c-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a915c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a915c-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a915c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a915c-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a915c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a915c-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a915c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a915c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a915c-118">See also</span></span>

- [<span data-ttu-id="a915c-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a915c-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
