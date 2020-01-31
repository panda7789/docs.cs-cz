---
title: ICorProfilerCallback::ClassUnloadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 75fb92be078c40f49ddcdc6662535b2a0be7a6ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866556"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="34302-102">ICorProfilerCallback::ClassUnloadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="34302-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="34302-103">Upozorní profileru, že je uvolněna třída.</span><span class="sxs-lookup"><span data-stu-id="34302-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34302-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34302-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34302-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="34302-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="34302-106">\[in] identifikuje třídu, která se uvolní.</span><span class="sxs-lookup"><span data-stu-id="34302-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="34302-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34302-107">Remarks</span></span>  
 <span data-ttu-id="34302-108">Hodnota `classId` není platná pro požadavek na informace po návratu metody `ClassUnloadStarted` – jedná se o poslední možnost profileru k získání informací o této třídě.</span><span class="sxs-lookup"><span data-stu-id="34302-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34302-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="34302-109">Requirements</span></span>  
 <span data-ttu-id="34302-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34302-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34302-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="34302-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34302-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="34302-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34302-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34302-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34302-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="34302-114">See also</span></span>

- [<span data-ttu-id="34302-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="34302-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="34302-116">ClassUnloadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="34302-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
