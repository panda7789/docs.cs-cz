---
title: ICorProfilerFunctionControl::SetILFunctionBody – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5b6cab555144c25c5984d74d19d5e81aa1a196d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454964"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="c8765-102">ICorProfilerFunctionControl::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="c8765-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="c8765-103">Nahrazuje tělo Common Intermediate Language (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="c8765-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8765-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8765-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8765-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8765-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="c8765-106">[in] Celková velikost nového CIL, včetně hlavičky a všech struktur za tělem.</span><span class="sxs-lookup"><span data-stu-id="c8765-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="c8765-107">[in] Ukazatel na novou hlavičku CIL.</span><span class="sxs-lookup"><span data-stu-id="c8765-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8765-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c8765-108">Return Value</span></span>  
 <span data-ttu-id="c8765-109">Tato metoda vrátí následující konkrétní HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c8765-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="c8765-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8765-110">HRESULT</span></span>|<span data-ttu-id="c8765-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c8765-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8765-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8765-112">S_OK</span></span>|<span data-ttu-id="c8765-113">Nahrazení proběhlo úspěšně.</span><span class="sxs-lookup"><span data-stu-id="c8765-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8765-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8765-114">Remarks</span></span>  
 <span data-ttu-id="c8765-115">Na rozdíl od [icorprofilerinfo::setilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody `SetILFunctionBody` metoda spravuje paměť vyžadovaná pro nový soubor CIL textu.</span><span class="sxs-lookup"><span data-stu-id="c8765-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="c8765-116">To znamená, že tělo CIL poskytované profileru nemá přidělování pomocí [imethodmalloc –](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) rozhraní nebo přidělené do určitého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="c8765-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="c8765-117">Může být přiděleno na kterékoli haldě.</span><span class="sxs-lookup"><span data-stu-id="c8765-117">It can be allocated on any heap.</span></span> <span data-ttu-id="c8765-118">Profileru můžete uvolnit paměť použitá pro jeho CIL textu po `SetILFunctionBody` vrátí.</span><span class="sxs-lookup"><span data-stu-id="c8765-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8765-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8765-119">Requirements</span></span>  
 <span data-ttu-id="c8765-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8765-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8765-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c8765-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c8765-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8765-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8765-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8765-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8765-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8765-124">See Also</span></span>  
 [<span data-ttu-id="c8765-125">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8765-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
