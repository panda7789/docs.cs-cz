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
ms.openlocfilehash: 096489fcdc9d604e003386501c22967b45ba6d7f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861096"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="90520-102">ICorProfilerObjectEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="90520-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="90520-103">Přesune kurzor tohoto čítače z aktuální pozice tak, aby byl zadaný počet prvků vynechán.</span><span class="sxs-lookup"><span data-stu-id="90520-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90520-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90520-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90520-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90520-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="90520-106">pro Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="90520-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90520-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90520-107">Remarks</span></span>  
 <span data-ttu-id="90520-108">Nová pozice kurzoru tohoto čítače výčtu je: (aktuální pozice) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="90520-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90520-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90520-109">Requirements</span></span>  
 <span data-ttu-id="90520-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90520-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90520-111">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="90520-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90520-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="90520-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90520-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90520-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90520-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90520-114">See also</span></span>

- [<span data-ttu-id="90520-115">ICorProfilerObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90520-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
