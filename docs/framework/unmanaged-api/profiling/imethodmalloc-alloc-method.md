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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66bd56a332dc34fd35f3129256cc0e3d6c5d4508
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636700"
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="54950-102">IMethodMalloc::Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="54950-102">IMethodMalloc::Alloc Method</span></span>

<span data-ttu-id="54950-103">Pokusí se přidělit zadanou velikost paměti pro nové tělo funkce Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="54950-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>

## <a name="syntax"></a><span data-ttu-id="54950-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54950-104">Syntax</span></span>

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a><span data-ttu-id="54950-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54950-105">Parameters</span></span>

`cb`\
<span data-ttu-id="54950-106">[in] Počet bajtů k přidělení pro tělo metody.</span><span class="sxs-lookup"><span data-stu-id="54950-106">[in] The number of bytes to allocate for the method body.</span></span>

## <a name="remarks"></a><span data-ttu-id="54950-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54950-107">Remarks</span></span>

 <span data-ttu-id="54950-108">Přidělená paměť se začne na adrese větší než základní adresy modulu, který je přidružený k této alokátoru.</span><span class="sxs-lookup"><span data-stu-id="54950-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="54950-109">Jinými slovy každý alokátoru pro konkrétního modulu se vytvoří a se pokusí o přidělení paměti na kladné posunu od jeho základní adresa.</span><span class="sxs-lookup"><span data-stu-id="54950-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="54950-110">Pokud `Alloc` se nepodařilo přidělit požadovaný počet bajtů na adrese větší než základní adresy modulu, vrátí E_OUTOFMEMORY, bez ohledu na skutečné množství paměti k dispozici.</span><span class="sxs-lookup"><span data-stu-id="54950-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>

 <span data-ttu-id="54950-111">`Alloc` Metoda byste měli použít ve spojení s [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="54950-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="54950-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54950-112">Requirements</span></span>
 <span data-ttu-id="54950-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54950-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="54950-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54950-114">**Header:** CorProf.idl, CorProf.h</span></span>

 <span data-ttu-id="54950-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54950-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="54950-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54950-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="54950-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54950-117">See also</span></span>

- [<span data-ttu-id="54950-118">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54950-118">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)
