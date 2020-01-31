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
ms.openlocfilehash: 15ce195af0c0e8f8777f6e5d02043e17e32308da
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866644"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="15a4a-102">ICorProfilerCallback::AssemblyLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="15a4a-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="15a4a-103">Upozorní profileru, že bylo dokončeno načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="15a4a-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15a4a-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15a4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15a4a-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="15a4a-106">\[v] identifikuje načtené sestavení.</span><span class="sxs-lookup"><span data-stu-id="15a4a-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="15a4a-107">\[in] hodnota HRESULT, která označuje, zda bylo sestavení úspěšně načteno.</span><span class="sxs-lookup"><span data-stu-id="15a4a-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="15a4a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15a4a-108">Remarks</span></span>  
 <span data-ttu-id="15a4a-109">Hodnota `assemblyId` není platná pro požadavek na informace, dokud není volána metoda `AssemblyLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="15a4a-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="15a4a-110">Některé části načtení sestavení mohou pokračovat po `AssemblyLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="15a4a-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="15a4a-111">Selhání HRESULT v `hrStatus` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="15a4a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="15a4a-112">Úspěšnost HRESULT v `hrStatus` však znamená, že první část načítání sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="15a4a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a4a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15a4a-113">Requirements</span></span>  
 <span data-ttu-id="15a4a-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15a4a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15a4a-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="15a4a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15a4a-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="15a4a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15a4a-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15a4a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a4a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15a4a-118">See also</span></span>

- [<span data-ttu-id="15a4a-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15a4a-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
