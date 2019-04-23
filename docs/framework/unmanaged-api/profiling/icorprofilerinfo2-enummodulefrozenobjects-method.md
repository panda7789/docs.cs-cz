---
title: ICorProfilerInfo2::EnumModuleFrozenObjects – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74517e034af6a1e4dfb8e4b28c2fec55a3d8de8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092835"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="c3ff0-102">ICorProfilerInfo2::EnumModuleFrozenObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="c3ff0-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="c3ff0-103">Získá enumerátor, který umožní iterace přes zmrazené objekty v zadaném modulu. Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ff0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3ff0-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3ff0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3ff0-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="c3ff0-106">[in] ID modulu, který obsahuje zmrazené objekty, které chcete vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="c3ff0-107">[out] Ukazatel na adresu [icorprofilerobjectenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) rozhraní, což vytvoří výčet zmrazené objekty.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ff0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3ff0-108">Requirements</span></span>  
 <span data-ttu-id="c3ff0-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3ff0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ff0-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3ff0-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3ff0-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3ff0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3ff0-112">**Verze rozhraní .NET framework:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span><span class="sxs-lookup"><span data-stu-id="c3ff0-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ff0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3ff0-113">See also</span></span>

- [<span data-ttu-id="c3ff0-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3ff0-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="c3ff0-115">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3ff0-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
