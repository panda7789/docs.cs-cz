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
ms.openlocfilehash: 77b07dae5b53db58b3628f677be1714e66ac18ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455254"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="99d46-102">ICorProfilerInfo2::EnumModuleFrozenObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="99d46-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="99d46-103">Získá enumerátor, který umožňuje iteraci přes ukotvené objekty v zadaný modul. Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="99d46-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99d46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99d46-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99d46-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99d46-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="99d46-106">[v] ID modul, který obsahuje ukotvené objekty, které chcete vytvořit její výčet.</span><span class="sxs-lookup"><span data-stu-id="99d46-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="99d46-107">[out] Ukazatel na adresu [icorprofilerobjectenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) rozhraní, které se zobrazí ukotvené objekty.</span><span class="sxs-lookup"><span data-stu-id="99d46-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99d46-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99d46-108">Requirements</span></span>  
 <span data-ttu-id="99d46-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99d46-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99d46-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="99d46-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="99d46-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99d46-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99d46-112">**Verze rozhraní .NET framework:** 3.5, 3.0 SP1, 3.0, 2.0 SP1 2.0</span><span class="sxs-lookup"><span data-stu-id="99d46-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d46-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="99d46-113">See Also</span></span>  
 [<span data-ttu-id="99d46-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99d46-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="99d46-115">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99d46-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
