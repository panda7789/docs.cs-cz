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
ms.openlocfilehash: bebc0cf6ac7912ea3a6641e0c729b759e865dac3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864658"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="c4150-102">ICorProfilerFunctionControl::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="c4150-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="c4150-103">Nahrazuje tělo Common Intermediate Language (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="c4150-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4150-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4150-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4150-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4150-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="c4150-106">[in] Celková velikost nového CIL, včetně hlavičky a všech struktur za tělem.</span><span class="sxs-lookup"><span data-stu-id="c4150-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="c4150-107">[in] Ukazatel na novou hlavičku CIL.</span><span class="sxs-lookup"><span data-stu-id="c4150-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4150-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c4150-108">Return Value</span></span>  
 <span data-ttu-id="c4150-109">Tato metoda vrátí následující konkrétní HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c4150-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="c4150-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4150-110">HRESULT</span></span>|<span data-ttu-id="c4150-111">Popis</span><span class="sxs-lookup"><span data-stu-id="c4150-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4150-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4150-112">S_OK</span></span>|<span data-ttu-id="c4150-113">Nahrazení proběhlo úspěšně.</span><span class="sxs-lookup"><span data-stu-id="c4150-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4150-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4150-114">Remarks</span></span>  
 <span data-ttu-id="c4150-115">Na rozdíl od metody [ICorProfilerInfo:: SetILFunctionBody –](icorprofilerinfo-setilfunctionbody-method.md) spravuje metoda `SetILFunctionBody` paměť potřebnou pro nový tělo CIL.</span><span class="sxs-lookup"><span data-stu-id="c4150-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="c4150-116">To znamená, že tělo CIL poskytnuté profilerem nemusí být přiděleno pomocí rozhraní [IMethodMalloc](imethodmalloc-interface.md) nebo přiděleno v určitém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="c4150-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="c4150-117">Může být přiděleno na kterékoli haldě.</span><span class="sxs-lookup"><span data-stu-id="c4150-117">It can be allocated on any heap.</span></span> <span data-ttu-id="c4150-118">Profiler může uvolnit paměť, která se používá pro tělo CIL po `SetILFunctionBody` vrátí.</span><span class="sxs-lookup"><span data-stu-id="c4150-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4150-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4150-119">Requirements</span></span>  
 <span data-ttu-id="c4150-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4150-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4150-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c4150-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4150-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c4150-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4150-123">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4150-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4150-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4150-124">See also</span></span>

- [<span data-ttu-id="c4150-125">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4150-125">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
