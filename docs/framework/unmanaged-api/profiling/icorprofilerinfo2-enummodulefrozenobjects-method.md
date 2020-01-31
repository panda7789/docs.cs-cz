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
ms.openlocfilehash: 27b3037459ac4f995e37515f6e96c28449c80a4f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862942"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="8eb02-102">ICorProfilerInfo2::EnumModuleFrozenObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="8eb02-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="8eb02-103">Získá enumerátor, který umožňuje iteraci přes zmrazené objekty v zadaném modulu. Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="8eb02-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8eb02-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eb02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8eb02-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="8eb02-106">pro ID modulu obsahujícího zmrazené objekty, které mají být vyčísleny</span><span class="sxs-lookup"><span data-stu-id="8eb02-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="8eb02-107">mimo Ukazatel na adresu rozhraní [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) , které vyčísluje zmrazené objekty.</span><span class="sxs-lookup"><span data-stu-id="8eb02-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eb02-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8eb02-108">Requirements</span></span>  
 <span data-ttu-id="8eb02-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb02-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb02-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8eb02-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8eb02-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8eb02-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eb02-112">**Verze .NET Framework:** 3,5, 3,0 SP1, 3,0, 2,0 SP1, 2,0</span><span class="sxs-lookup"><span data-stu-id="8eb02-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb02-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8eb02-113">See also</span></span>

- [<span data-ttu-id="8eb02-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8eb02-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8eb02-115">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8eb02-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
