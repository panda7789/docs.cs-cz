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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f08b3d9634362d47615fe14287ab9ec35e78ee65
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775053"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="91b35-102">ICorProfilerObjectEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="91b35-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="91b35-103">Získá celkový počet zmrazené objekty v kolekci.</span><span class="sxs-lookup"><span data-stu-id="91b35-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91b35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91b35-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91b35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91b35-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="91b35-106">[out] Ukazatel na počet zmrazené objekty v kolekci.</span><span class="sxs-lookup"><span data-stu-id="91b35-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="91b35-107">Tato metoda vždy vrátí nulu v rozhraní .NET Framework verze 3.5 Service Pack 1 (SP1) a novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="91b35-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91b35-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91b35-108">Requirements</span></span>  
 <span data-ttu-id="91b35-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91b35-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91b35-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91b35-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="91b35-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91b35-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91b35-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91b35-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91b35-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91b35-113">See also</span></span>

- [<span data-ttu-id="91b35-114">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91b35-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
