---
title: ICorProfilerObjectEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
ms.openlocfilehash: 077e6d729eb98ddad25cd0c0cccf6d4641e2602c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428258"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="608d0-102">ICorProfilerObjectEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="608d0-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="608d0-103">Získá celkový počet zmrazených objektů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="608d0-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="608d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="608d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="608d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="608d0-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="608d0-106">mimo Ukazatel na počet zmrazených objektů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="608d0-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="608d0-107">Tato metoda vždycky vrátí nulu v .NET Framework verze 3,5 Service Pack 1 (SP1) a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="608d0-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="608d0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="608d0-108">Requirements</span></span>  
 <span data-ttu-id="608d0-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="608d0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="608d0-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="608d0-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="608d0-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="608d0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="608d0-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="608d0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="608d0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="608d0-113">See also</span></span>

- [<span data-ttu-id="608d0-114">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="608d0-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
