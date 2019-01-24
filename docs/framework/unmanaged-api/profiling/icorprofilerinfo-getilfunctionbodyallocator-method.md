---
title: ICorProfilerInfo::GetILFunctionBodyAllocator – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ae8b209ad03594cb77029193b0e9dec773a6e02
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603323"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="6e985-102">ICorProfilerInfo::GetILFunctionBodyAllocator – metoda</span><span class="sxs-lookup"><span data-stu-id="6e985-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="6e985-103">Získá rozhraní, které představuje způsob, jak přidělit paměť pro záměnu těla metody v kódu Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="6e985-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e985-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e985-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e985-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e985-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="6e985-106">[in] ID modulu, ve kterém se nachází metodu.</span><span class="sxs-lookup"><span data-stu-id="6e985-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="6e985-107">[out] Ukazatel [imethodmalloc –](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) rozhraní, které poskytuje metodu pro přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="6e985-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e985-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e985-108">Remarks</span></span>  
 <span data-ttu-id="6e985-109">Tělo metody v kódu jazyka MSIL musí být umístěn jako relativní virtuální adresu (RVA), relativní k načteného modulu, což znamená, že následuje modul v rámci 4 GB.</span><span class="sxs-lookup"><span data-stu-id="6e985-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="6e985-110">Aby bylo snazší pro nástroj vyměnit tělo metody, `GetILFunctionBodyAllocator` metoda zajišťuje, že paměť je přidělena v tomto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="6e985-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e985-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e985-111">Requirements</span></span>  
 <span data-ttu-id="6e985-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e985-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e985-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e985-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e985-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e985-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e985-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e985-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e985-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e985-116">See also</span></span>
- [<span data-ttu-id="6e985-117">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e985-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
