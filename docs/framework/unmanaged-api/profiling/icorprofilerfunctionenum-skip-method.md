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
ms.openlocfilehash: 5f4ef55561c23997fca51dc7d463e2eefdba7d65
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864307"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="d693b-102">ICorProfilerFunctionEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="d693b-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="d693b-103">Posune kurzor čítače výčtu z aktuální pozice tak, aby byl zadaný počet prvků vynechán.</span><span class="sxs-lookup"><span data-stu-id="d693b-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d693b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d693b-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d693b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d693b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d693b-106">pro Počet prvků, které mají být přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="d693b-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d693b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d693b-107">Return Value</span></span>  
 <span data-ttu-id="d693b-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="d693b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d693b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d693b-109">HRESULT</span></span>|<span data-ttu-id="d693b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d693b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d693b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d693b-111">S_OK</span></span>|<span data-ttu-id="d693b-112">prvky `celt` byly přeskočeny.</span><span class="sxs-lookup"><span data-stu-id="d693b-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="d693b-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d693b-113">S_FALSE</span></span>|<span data-ttu-id="d693b-114">Méně než `celt` prvky byly přeskočeny, což znamená, že žádné další prvky nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d693b-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d693b-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d693b-115">Remarks</span></span>  
 <span data-ttu-id="d693b-116">Nová pozice kurzoru tohoto enumerátoru je (aktuální pozice) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="d693b-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d693b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d693b-117">Requirements</span></span>  
 <span data-ttu-id="d693b-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d693b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d693b-119">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d693b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d693b-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d693b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d693b-121">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d693b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d693b-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d693b-122">See also</span></span>

- [<span data-ttu-id="d693b-123">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d693b-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="d693b-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d693b-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
