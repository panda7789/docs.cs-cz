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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bcc837fede7e7db59bdf88a0b5434a7c1924335
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597109"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="4d7df-102">ICorProfilerObjectEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="4d7df-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="4d7df-103">Posune kurzor výčet z aktuálního umístění tak, aby zadaný počet prvků, které se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="4d7df-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d7df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d7df-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d7df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d7df-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4d7df-106">[in] Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="4d7df-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d7df-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d7df-107">Remarks</span></span>  
 <span data-ttu-id="4d7df-108">Nová pozice kurzoru tento výčet je: (aktuální pozici) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="4d7df-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d7df-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d7df-109">Requirements</span></span>  
 <span data-ttu-id="4d7df-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d7df-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d7df-111">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4d7df-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d7df-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d7df-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d7df-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d7df-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d7df-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d7df-114">See also</span></span>

- [<span data-ttu-id="4d7df-115">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d7df-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
