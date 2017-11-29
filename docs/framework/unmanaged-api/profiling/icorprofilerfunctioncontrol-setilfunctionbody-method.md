---
title: "ICorProfilerFunctionControl::SetILFunctionBody – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9469435186a5aef130ca4ebef27a4613afeb921c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="8a06b-102">ICorProfilerFunctionControl::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="8a06b-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="8a06b-103">Nahrazuje tělo Common Intermediate Language (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="8a06b-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a06b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a06b-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a06b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a06b-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="8a06b-106">[in] Celková velikost nového CIL, včetně hlavičky a všech struktur za tělem.</span><span class="sxs-lookup"><span data-stu-id="8a06b-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="8a06b-107">[in] Ukazatel na novou hlavičku CIL.</span><span class="sxs-lookup"><span data-stu-id="8a06b-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a06b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8a06b-108">Return Value</span></span>  
 <span data-ttu-id="8a06b-109">Tato metoda vrátí následující konkrétní HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8a06b-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="8a06b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a06b-110">HRESULT</span></span>|<span data-ttu-id="8a06b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="8a06b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a06b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a06b-112">S_OK</span></span>|<span data-ttu-id="8a06b-113">Nahrazení proběhlo úspěšně.</span><span class="sxs-lookup"><span data-stu-id="8a06b-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a06b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a06b-114">Remarks</span></span>  
 <span data-ttu-id="8a06b-115">Na rozdíl od [icorprofilerinfo::setilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody `SetILFunctionBody` metoda spravuje paměť vyžadovaná pro nový soubor CIL textu.</span><span class="sxs-lookup"><span data-stu-id="8a06b-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="8a06b-116">To znamená, že tělo CIL poskytované profileru nemá přidělování pomocí [imethodmalloc –](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) rozhraní nebo přidělené do určitého rozsahu.</span><span class="sxs-lookup"><span data-stu-id="8a06b-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="8a06b-117">Může být přiděleno na kterékoli haldě.</span><span class="sxs-lookup"><span data-stu-id="8a06b-117">It can be allocated on any heap.</span></span> <span data-ttu-id="8a06b-118">Profileru můžete uvolnit paměť použitá pro jeho CIL textu po `SetILFunctionBody` vrátí.</span><span class="sxs-lookup"><span data-stu-id="8a06b-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a06b-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a06b-119">Requirements</span></span>  
 <span data-ttu-id="8a06b-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a06b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a06b-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a06b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a06b-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a06b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a06b-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a06b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a06b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a06b-124">See Also</span></span>  
 [<span data-ttu-id="8a06b-125">Icorprofilerfunctioncontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8a06b-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
