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
ms.openlocfilehash: a1a616c1289867864eb9eb449c7d6f47f9a8352b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861291"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="3989f-102">ICorProfilerObjectEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="3989f-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="3989f-103">Získá celkový počet zmrazených objektů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="3989f-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3989f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3989f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3989f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3989f-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="3989f-106">mimo Ukazatel na počet zmrazených objektů v kolekci.</span><span class="sxs-lookup"><span data-stu-id="3989f-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="3989f-107">Tato metoda vždycky vrátí nulu v .NET Framework verze 3,5 Service Pack 1 (SP1) a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="3989f-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3989f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3989f-108">Requirements</span></span>  
 <span data-ttu-id="3989f-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3989f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3989f-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3989f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3989f-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3989f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3989f-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3989f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3989f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3989f-113">See also</span></span>

- [<span data-ttu-id="3989f-114">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3989f-114">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
