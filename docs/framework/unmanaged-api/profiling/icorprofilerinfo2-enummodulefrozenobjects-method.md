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
ms.openlocfilehash: 1fe44f8f84c079e920c8c82fb9d52d1980d3b852
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497202"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="60cfa-102">ICorProfilerInfo2::EnumModuleFrozenObjects – metoda</span><span class="sxs-lookup"><span data-stu-id="60cfa-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="60cfa-103">Získá enumerátor, který umožňuje iteraci přes zmrazené objekty v zadaném modulu. Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="60cfa-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60cfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60cfa-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60cfa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60cfa-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="60cfa-106">pro ID modulu obsahujícího zmrazené objekty, které mají být vyčísleny</span><span class="sxs-lookup"><span data-stu-id="60cfa-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="60cfa-107">mimo Ukazatel na adresu rozhraní [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) , které vyčísluje zmrazené objekty.</span><span class="sxs-lookup"><span data-stu-id="60cfa-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60cfa-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60cfa-108">Requirements</span></span>  
 <span data-ttu-id="60cfa-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60cfa-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60cfa-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="60cfa-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60cfa-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="60cfa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60cfa-112">**Verze .NET Framework:** 3,5, 3,0 SP1, 3,0, 2,0 SP1, 2,0</span><span class="sxs-lookup"><span data-stu-id="60cfa-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60cfa-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60cfa-113">See also</span></span>

- [<span data-ttu-id="60cfa-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60cfa-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="60cfa-115">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60cfa-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
