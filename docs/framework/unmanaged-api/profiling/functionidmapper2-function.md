---
title: FunctionIDMapper2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: 7f83469920956d73a275f510b0d3c3e94a4caa8d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440680"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="328c8-102">FunctionIDMapper2 – funkce</span><span class="sxs-lookup"><span data-stu-id="328c8-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="328c8-103">Upozorní profileru, že daný identifikátor funkce může být přemapován na alternativní ID, které se má použít v [FunctionEnter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)a [FunctionTailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), nebo[Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)a zpětná volání [FunctionTailcall3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) pro danou funkci.</span><span class="sxs-lookup"><span data-stu-id="328c8-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="328c8-104">`FunctionIDMapper2` také umožňuje profileru označit, zda chce přijímat zpětná volání této funkce.</span><span class="sxs-lookup"><span data-stu-id="328c8-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="328c8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="328c8-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="328c8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="328c8-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="328c8-107">pro Identifikátor funkce, která má být přemapována.</span><span class="sxs-lookup"><span data-stu-id="328c8-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="328c8-108">pro Ukazatel na data, která se používají k jednoznačnému rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="328c8-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="328c8-109">mimo Ukazatel na hodnotu, kterou Profiler nastaví na `true`, pokud chce přijmout `FunctionEnter3`, `FunctionLeave3`a `FunctionTailcall3`nebo `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`a `FunctionTailcall3WithInfo` zpětná volání; v opačném případě nastaví tuto hodnotu na `false`.</span><span class="sxs-lookup"><span data-stu-id="328c8-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="328c8-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="328c8-110">Return Value</span></span>  
 <span data-ttu-id="328c8-111">Profiler vrátí hodnotu, kterou spouštěcí modul používá jako alternativní identifikátor funkce.</span><span class="sxs-lookup"><span data-stu-id="328c8-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="328c8-112">Návratová hodnota nemůže být null, pokud není vráceno `false` v `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="328c8-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="328c8-113">V opačném případě návratová hodnota null vytvoří nepředvídatelné výsledky, včetně možného zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="328c8-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="328c8-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="328c8-114">Remarks</span></span>  
 <span data-ttu-id="328c8-115">Tato metoda rozšiřuje funkci [FunctionIDMapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) o další parametr, který se používá k předání dat klienta.</span><span class="sxs-lookup"><span data-stu-id="328c8-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="328c8-116">Data klienta slouží k jednoznačnému rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="328c8-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="328c8-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="328c8-117">Requirements</span></span>  
 <span data-ttu-id="328c8-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="328c8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="328c8-119">**Hlavička:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="328c8-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="328c8-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="328c8-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="328c8-121">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="328c8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="328c8-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="328c8-122">See also</span></span>

- [<span data-ttu-id="328c8-123">ICorProfilerInfo:: SetFunctionIDMapper –</span><span class="sxs-lookup"><span data-stu-id="328c8-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="328c8-124">ICorProfilerInfo3:: Setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="328c8-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="328c8-125">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="328c8-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="328c8-126">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="328c8-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="328c8-127">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="328c8-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="328c8-128">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="328c8-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="328c8-129">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="328c8-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="328c8-130">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="328c8-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="328c8-131">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="328c8-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
