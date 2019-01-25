---
title: ICorProfilerCallback::ClassLoadStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a10ea7b257059d2b3177698e8d663a0c28e262b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737069"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="29ce3-102">ICorProfilerCallback::ClassLoadStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="29ce3-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="29ce3-103">Načtení třídy oznámí profileru.</span><span class="sxs-lookup"><span data-stu-id="29ce3-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ce3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29ce3-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29ce3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29ce3-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="29ce3-106">[in] Určuje třídu, která se načítá.</span><span class="sxs-lookup"><span data-stu-id="29ce3-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29ce3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29ce3-107">Remarks</span></span>  
 <span data-ttu-id="29ce3-108">Hodnota `classId` není platná pro požadavek informace do [icorprofilercallback::classloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="29ce3-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ce3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29ce3-109">Requirements</span></span>  
 <span data-ttu-id="29ce3-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29ce3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ce3-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29ce3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29ce3-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29ce3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29ce3-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ce3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ce3-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29ce3-114">See also</span></span>
- [<span data-ttu-id="29ce3-115">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29ce3-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
