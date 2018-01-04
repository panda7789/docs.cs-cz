---
title: "ICorProfilerInfo::GetILFunctionBodyAllocator – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBodyAllocator
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1feec20f0ddc4f6029490e06d4729b3fdaa7fa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="6d2cf-102">ICorProfilerInfo::GetILFunctionBodyAllocator – metoda</span><span class="sxs-lookup"><span data-stu-id="6d2cf-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="6d2cf-103">Získá rozhraní, které poskytuje metodu pro přidělení paměti, který se má použít pro odkládací out těla metody v kódu (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6d2cf-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d2cf-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d2cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d2cf-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="6d2cf-106">[v] ID modulu, ve kterém se nachází metoda.</span><span class="sxs-lookup"><span data-stu-id="6d2cf-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="6d2cf-107">[out] Ukazatel na [imethodmalloc –](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) rozhraní, které poskytuje metodu, jak přidělit paměť.</span><span class="sxs-lookup"><span data-stu-id="6d2cf-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d2cf-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d2cf-108">Remarks</span></span>  
 <span data-ttu-id="6d2cf-109">Metoda text v kódu MSIL musí být umístěn jako relativní virtuální adresy (RVA), relativně k načíst modul, což znamená, že postupuje modul v rámci 4 GB.</span><span class="sxs-lookup"><span data-stu-id="6d2cf-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="6d2cf-110">Aby bylo snazší pro nástroj vyměnit těla metody, `GetILFunctionBodyAllocator` metoda zajišťuje, že paměť je přidělená v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="6d2cf-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d2cf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d2cf-111">Requirements</span></span>  
 <span data-ttu-id="6d2cf-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d2cf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d2cf-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d2cf-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d2cf-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d2cf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d2cf-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d2cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2cf-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d2cf-116">See Also</span></span>  
 [<span data-ttu-id="6d2cf-117">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d2cf-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
