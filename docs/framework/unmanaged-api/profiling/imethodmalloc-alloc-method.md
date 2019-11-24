---
title: IMethodMalloc::Alloc – metoda
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
ms.openlocfilehash: af881d23ff77f05dadbbc745b973979e35ebe9f7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447565"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="7e26e-102">IMethodMalloc::Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="7e26e-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="7e26e-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span><span class="sxs-lookup"><span data-stu-id="7e26e-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e26e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e26e-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="7e26e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e26e-105">Parameters</span></span>

`cb`\
<span data-ttu-id="7e26e-106">[in] The number of bytes to allocate for the method body.</span><span class="sxs-lookup"><span data-stu-id="7e26e-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e26e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e26e-107">Remarks</span></span>

 <span data-ttu-id="7e26e-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span><span class="sxs-lookup"><span data-stu-id="7e26e-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="7e26e-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span><span class="sxs-lookup"><span data-stu-id="7e26e-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="7e26e-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span><span class="sxs-lookup"><span data-stu-id="7e26e-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="7e26e-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="7e26e-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e26e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e26e-112">Requirements</span></span>
 <span data-ttu-id="7e26e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e26e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="7e26e-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e26e-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="7e26e-115">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e26e-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="7e26e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e26e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7e26e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e26e-117">See also</span></span>

- [<span data-ttu-id="7e26e-118">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e26e-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
