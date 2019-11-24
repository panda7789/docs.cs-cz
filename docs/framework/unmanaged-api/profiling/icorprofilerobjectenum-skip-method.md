---
title: ICorProfilerObjectEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
ms.openlocfilehash: 3c573c709e765fa723a726f5c8990ba59222ed1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428129"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="62f0d-102">ICorProfilerObjectEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="62f0d-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="62f0d-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span><span class="sxs-lookup"><span data-stu-id="62f0d-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62f0d-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62f0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62f0d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="62f0d-106">[in] The number of elements to be skipped.</span><span class="sxs-lookup"><span data-stu-id="62f0d-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62f0d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62f0d-107">Remarks</span></span>  
 <span data-ttu-id="62f0d-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="62f0d-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62f0d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="62f0d-109">Requirements</span></span>  
 <span data-ttu-id="62f0d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62f0d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62f0d-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62f0d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62f0d-112">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62f0d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62f0d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62f0d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f0d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62f0d-114">See also</span></span>

- [<span data-ttu-id="62f0d-115">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="62f0d-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
