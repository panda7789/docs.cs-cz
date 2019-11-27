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
ms.openlocfilehash: 33b72c8d089e5b335069fe465987086dfa1243bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445167"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="f2a98-102">ICorProfilerCallback::AssemblyLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="f2a98-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="f2a98-103">Upozorní profileru, že bylo dokončeno načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2a98-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2a98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2a98-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2a98-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2a98-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="f2a98-106">pro Identifikuje sestavení, které bylo načteno.</span><span class="sxs-lookup"><span data-stu-id="f2a98-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f2a98-107">pro Hodnota HRESULT, která označuje, zda bylo sestavení úspěšně načteno.</span><span class="sxs-lookup"><span data-stu-id="f2a98-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2a98-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2a98-108">Remarks</span></span>  
 <span data-ttu-id="f2a98-109">Hodnota `assemblyId` není platná pro požadavek na informace, dokud není volána metoda `AssemblyLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="f2a98-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="f2a98-110">Některé části načtení sestavení mohou pokračovat po `AssemblyLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f2a98-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="f2a98-111">Selhání HRESULT v `hrStatus` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="f2a98-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f2a98-112">Úspěšnost HRESULT v `hrStatus` však znamená, že první část načítání sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="f2a98-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2a98-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2a98-113">Requirements</span></span>  
 <span data-ttu-id="f2a98-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2a98-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2a98-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f2a98-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2a98-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f2a98-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2a98-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2a98-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a98-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2a98-118">See also</span></span>

- [<span data-ttu-id="f2a98-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2a98-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
