---
title: ICorProfilerCallback::ClassLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: e0ff90f99c1127b5a4626f47514ba7099b5d48af
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866595"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="2bed1-102">ICorProfilerCallback::ClassLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="2bed1-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="2bed1-103">Upozorní profileru, že se dokončilo načítání třídy.</span><span class="sxs-lookup"><span data-stu-id="2bed1-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bed1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bed1-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bed1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2bed1-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="2bed1-106">\[v] identifikuje třídu, která byla načtena.</span><span class="sxs-lookup"><span data-stu-id="2bed1-106">\[in] Identifies the class that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="2bed1-107">\[in] hodnota HRESULT, která označuje, jestli se třída úspěšně načetla.</span><span class="sxs-lookup"><span data-stu-id="2bed1-107">\[in] An HRESULT that indicates whether the class loaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="2bed1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bed1-108">Remarks</span></span>  
 <span data-ttu-id="2bed1-109">Hodnota `classId` není platná pro požadavek na informace, dokud není volána metoda `ClassLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="2bed1-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="2bed1-110">Některé části načtení třídy mohou pokračovat po `ClassLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2bed1-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="2bed1-111">Selhání HRESULT v `hrStatus` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="2bed1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="2bed1-112">Úspěšnost HRESULT v `hrStatus` však znamená, že první část načtení třídy byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="2bed1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bed1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bed1-113">Requirements</span></span>  
 <span data-ttu-id="2bed1-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bed1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bed1-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2bed1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2bed1-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2bed1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bed1-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bed1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bed1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bed1-118">See also</span></span>

- [<span data-ttu-id="2bed1-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bed1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2bed1-120">ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="2bed1-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
