---
title: ICorProfilerFunctionEnum::Skip – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba1f357c0d68b5a8b5104569a95433504cc84ee6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675330"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="60659-102">ICorProfilerFunctionEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="60659-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="60659-103">Posune kurzor enumerátor z aktuálního umístění tak, aby zadaný počet prvků, které se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="60659-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60659-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60659-104">Syntax</span></span>  
  
```  
HRESULT Skip([in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60659-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60659-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="60659-106">[in] Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="60659-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60659-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="60659-107">Return Value</span></span>  
 <span data-ttu-id="60659-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="60659-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="60659-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60659-109">HRESULT</span></span>|<span data-ttu-id="60659-110">Popis</span><span class="sxs-lookup"><span data-stu-id="60659-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60659-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="60659-111">S_OK</span></span>|<span data-ttu-id="60659-112">`celt` elementy byly vynechány.</span><span class="sxs-lookup"><span data-stu-id="60659-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="60659-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="60659-113">S_FALSE</span></span>|<span data-ttu-id="60659-114">Méně než `celt` prvky byly přeskočeny, což znamená, že neexistují žádné další prvky.</span><span class="sxs-lookup"><span data-stu-id="60659-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60659-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60659-115">Remarks</span></span>  
 <span data-ttu-id="60659-116">Nové pozice kurzoru tento výčet je (aktuální pozici) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="60659-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60659-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60659-117">Requirements</span></span>  
 <span data-ttu-id="60659-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60659-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60659-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60659-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60659-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60659-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60659-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60659-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60659-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60659-122">See also</span></span>
- [<span data-ttu-id="60659-123">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60659-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="60659-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="60659-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
