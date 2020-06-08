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
ms.openlocfilehash: a6b24fd59a183a4a59b117663772417d55cc67db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503134"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="952b2-102">ICorProfilerFunctionControl::SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="952b2-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="952b2-103">Nahrazuje tělo Common Intermediate Language (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="952b2-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="952b2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="952b2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="952b2-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="952b2-106">[in] Celková velikost nového CIL, včetně hlavičky a všech struktur za tělem.</span><span class="sxs-lookup"><span data-stu-id="952b2-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="952b2-107">[in] Ukazatel na novou hlavičku CIL.</span><span class="sxs-lookup"><span data-stu-id="952b2-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="952b2-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="952b2-108">Return Value</span></span>  
 <span data-ttu-id="952b2-109">Tato metoda vrátí následující konkrétní HRESULT.</span><span class="sxs-lookup"><span data-stu-id="952b2-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="952b2-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="952b2-110">HRESULT</span></span>|<span data-ttu-id="952b2-111">Description</span><span class="sxs-lookup"><span data-stu-id="952b2-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="952b2-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="952b2-112">S_OK</span></span>|<span data-ttu-id="952b2-113">Nahrazení proběhlo úspěšně.</span><span class="sxs-lookup"><span data-stu-id="952b2-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="952b2-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="952b2-114">Remarks</span></span>  
 <span data-ttu-id="952b2-115">Na rozdíl od metody [ICorProfilerInfo:: SetILFunctionBody –](icorprofilerinfo-setilfunctionbody-method.md) `SetILFunctionBody` spravuje metoda paměť potřebnou pro nový tělo CIL.</span><span class="sxs-lookup"><span data-stu-id="952b2-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="952b2-116">To znamená, že tělo CIL poskytnuté profilerem nemusí být přiděleno pomocí rozhraní [IMethodMalloc](imethodmalloc-interface.md) nebo přiděleno v určitém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="952b2-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="952b2-117">Může být přiděleno na kterékoli haldě.</span><span class="sxs-lookup"><span data-stu-id="952b2-117">It can be allocated on any heap.</span></span> <span data-ttu-id="952b2-118">Profiler může uvolnit paměť, která se používá pro tělo CIL po `SetILFunctionBody` vrácení.</span><span class="sxs-lookup"><span data-stu-id="952b2-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="952b2-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="952b2-119">Requirements</span></span>  
 <span data-ttu-id="952b2-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="952b2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="952b2-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="952b2-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="952b2-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="952b2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="952b2-123">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="952b2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952b2-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="952b2-124">See also</span></span>

- [<span data-ttu-id="952b2-125">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="952b2-125">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
