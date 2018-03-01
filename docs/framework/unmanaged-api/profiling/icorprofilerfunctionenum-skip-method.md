---
title: "ICorProfilerFunctionEnum::Skip – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ddde6069072092cfc0441686ce4d53aa0a4bd534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="8bcac-102">ICorProfilerFunctionEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="8bcac-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="8bcac-103">Posune kurzor enumerátor z aktuálního umístění tak, aby se přeskočí zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="8bcac-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bcac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bcac-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8bcac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bcac-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8bcac-106">[v] Počet elementů lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="8bcac-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bcac-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8bcac-107">Return Value</span></span>  
 <span data-ttu-id="8bcac-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="8bcac-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8bcac-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8bcac-109">HRESULT</span></span>|<span data-ttu-id="8bcac-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8bcac-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8bcac-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8bcac-111">S_OK</span></span>|<span data-ttu-id="8bcac-112">`celt`elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="8bcac-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="8bcac-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8bcac-113">S_FALSE</span></span>|<span data-ttu-id="8bcac-114">Méně než `celt` elementy byly přeskočeny, což naznačuje, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="8bcac-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bcac-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bcac-115">Remarks</span></span>  
 <span data-ttu-id="8bcac-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="8bcac-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bcac-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8bcac-117">Requirements</span></span>  
 <span data-ttu-id="8bcac-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bcac-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bcac-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8bcac-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8bcac-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bcac-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bcac-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bcac-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bcac-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bcac-122">See Also</span></span>  
 [<span data-ttu-id="8bcac-123">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8bcac-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="8bcac-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="8bcac-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
