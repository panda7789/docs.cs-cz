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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d96f9853cfac8cef7b8af2e80b2e5d4196cdf79d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480218"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="a1676-102">ICorProfilerCallback::ClassLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="a1676-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="a1676-103">Třída dokončení načítání oznámí profileru.</span><span class="sxs-lookup"><span data-stu-id="a1676-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1676-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1676-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1676-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1676-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="a1676-106">[in] Určuje třídu, která byla načtena.</span><span class="sxs-lookup"><span data-stu-id="a1676-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="a1676-107">[in] HRESULT, která určuje, zda třída úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="a1676-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1676-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1676-108">Remarks</span></span>  
 <span data-ttu-id="a1676-109">Hodnota `classId` není platná pro požadavek informace do `ClassLoadFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="a1676-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="a1676-110">Některé části načítání třídy může pokračovat po `ClassLoadFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a1676-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="a1676-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="a1676-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="a1676-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část načítání třídy proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="a1676-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1676-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1676-113">Requirements</span></span>  
 <span data-ttu-id="a1676-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1676-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1676-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1676-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1676-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1676-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1676-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1676-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1676-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1676-118">See also</span></span>
- [<span data-ttu-id="a1676-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1676-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a1676-120">ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="a1676-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
