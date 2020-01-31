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
ms.openlocfilehash: 5fe472c4a0053ec9e37d7d61ffde5cf21d65dd2f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863462"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="26935-102">ICorProfilerInfo::GetILFunctionBodyAllocator – metoda</span><span class="sxs-lookup"><span data-stu-id="26935-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="26935-103">Získá rozhraní, které poskytuje metodu pro přidělení paměti, která se má použít pro odměnu těla metody v kódu jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="26935-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26935-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26935-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26935-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26935-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="26935-106">pro ID modulu, ve kterém je metoda umístěna.</span><span class="sxs-lookup"><span data-stu-id="26935-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="26935-107">mimo Ukazatel na rozhraní [IMethodMalloc](imethodmalloc-interface.md) , které poskytuje metodu pro přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="26935-107">[out] A pointer to an [IMethodMalloc](imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26935-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26935-108">Remarks</span></span>  
 <span data-ttu-id="26935-109">Tělo metody v kódu jazyka MSIL musí být umístěno jako relativní virtuální adresa (RVA), relativně k zadanému modulu, což znamená, že se za modul skládá ze 4 GB.</span><span class="sxs-lookup"><span data-stu-id="26935-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="26935-110">Aby nástroj mohl snadno vyměňovat tělo metody, metoda `GetILFunctionBodyAllocator` zajistí, aby se paměť v tomto rozsahu přidělila.</span><span class="sxs-lookup"><span data-stu-id="26935-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26935-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26935-111">Requirements</span></span>  
 <span data-ttu-id="26935-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26935-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26935-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="26935-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26935-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="26935-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26935-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26935-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26935-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26935-116">See also</span></span>

- [<span data-ttu-id="26935-117">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26935-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
