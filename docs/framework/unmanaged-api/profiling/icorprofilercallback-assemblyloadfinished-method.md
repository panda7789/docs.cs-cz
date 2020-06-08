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
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500439"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="ff8bf-102">ICorProfilerCallback::AssemblyLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="ff8bf-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="ff8bf-103">Upozorní profileru, že bylo dokončeno načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff8bf-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff8bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff8bf-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff8bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff8bf-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="ff8bf-106">\[v] identifikuje sestavení, které bylo načteno.</span><span class="sxs-lookup"><span data-stu-id="ff8bf-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="ff8bf-107">\[in] HRESULT, který označuje, zda bylo sestavení úspěšně načteno.</span><span class="sxs-lookup"><span data-stu-id="ff8bf-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff8bf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff8bf-108">Remarks</span></span>  
 <span data-ttu-id="ff8bf-109">Hodnota `assemblyId` není platná pro požadavek na informace, dokud `AssemblyLoadFinished` není volána metoda.</span><span class="sxs-lookup"><span data-stu-id="ff8bf-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="ff8bf-110">Některé části načtení sestavení mohou pokračovat po `AssemblyLoadFinished` zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="ff8bf-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="ff8bf-111">Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání.</span><span class="sxs-lookup"><span data-stu-id="ff8bf-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ff8bf-112">Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část načítání sestavení byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="ff8bf-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff8bf-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff8bf-113">Requirements</span></span>  
 <span data-ttu-id="ff8bf-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff8bf-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff8bf-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ff8bf-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff8bf-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ff8bf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff8bf-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff8bf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8bf-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff8bf-118">See also</span></span>

- [<span data-ttu-id="ff8bf-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff8bf-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
