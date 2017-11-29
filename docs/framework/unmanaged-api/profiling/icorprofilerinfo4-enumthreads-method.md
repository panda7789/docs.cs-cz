---
title: "ICorProfilerInfo4::EnumThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.EnumThreads
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 20022a3b7353c0e43aaa44e368c06cd79906956e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="04cab-102">ICorProfilerInfo4::EnumThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="04cab-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="04cab-103">Vrátí enumerátor, který poskytuje metody pro postupně iteraci prostřednictvím kolekce všech spravovaných vláken v procesu PROFILOVANÉHO.</span><span class="sxs-lookup"><span data-stu-id="04cab-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04cab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04cab-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04cab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04cab-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="04cab-106">[out] Ukazatel na [icorprofilerthreadenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="04cab-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04cab-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04cab-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04cab-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04cab-108">Requirements</span></span>  
 <span data-ttu-id="04cab-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04cab-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04cab-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04cab-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04cab-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04cab-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04cab-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04cab-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04cab-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="04cab-113">See Also</span></span>  
 [<span data-ttu-id="04cab-114">Icorprofilerthreadenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04cab-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="04cab-115">Icorprofilerinfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04cab-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="04cab-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="04cab-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="04cab-117">Profilace</span><span class="sxs-lookup"><span data-stu-id="04cab-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
