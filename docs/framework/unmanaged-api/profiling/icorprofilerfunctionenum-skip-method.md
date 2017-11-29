---
title: "ICorProfilerFunctionEnum::Skip – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Skip Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c5142b091ec32c162daaca9c53cb65763bb5ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="eab48-102">ICorProfilerFunctionEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="eab48-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="eab48-103">Posune kurzor enumerátor z aktuálního umístění tak, aby se přeskočí zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="eab48-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eab48-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eab48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eab48-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="eab48-106">[v] Počet elementů lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="eab48-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eab48-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="eab48-107">Return Value</span></span>  
 <span data-ttu-id="eab48-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="eab48-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="eab48-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eab48-109">HRESULT</span></span>|<span data-ttu-id="eab48-110">Popis</span><span class="sxs-lookup"><span data-stu-id="eab48-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eab48-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="eab48-111">S_OK</span></span>|<span data-ttu-id="eab48-112">`celt`elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="eab48-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="eab48-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="eab48-113">S_FALSE</span></span>|<span data-ttu-id="eab48-114">Méně než `celt` elementy byly přeskočeny, což naznačuje, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="eab48-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eab48-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eab48-115">Remarks</span></span>  
 <span data-ttu-id="eab48-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="eab48-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab48-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eab48-117">Requirements</span></span>  
 <span data-ttu-id="eab48-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eab48-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eab48-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eab48-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eab48-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eab48-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eab48-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eab48-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab48-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="eab48-122">See Also</span></span>  
 [<span data-ttu-id="eab48-123">Icorprofilerfunctionenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eab48-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="eab48-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="eab48-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
