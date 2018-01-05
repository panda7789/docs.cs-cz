---
title: "IMethodMalloc::Alloc – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc.Alloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26998e8b2e8648b4fb175f188540e7bc33c580c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="346e2-102">IMethodMalloc::Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="346e2-102">IMethodMalloc::Alloc Method</span></span>
<span data-ttu-id="346e2-103">Pokusí se přidělit zadanou velikost paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="346e2-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="346e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="346e2-104">Syntax</span></span>  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="346e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="346e2-105">Parameters</span></span>  
 `cb`  
 <span data-ttu-id="346e2-106">[v] Počet bajtů k přidělení pro tělo metoda.</span><span class="sxs-lookup"><span data-stu-id="346e2-106">[in] The number of bytes to allocate for the method body.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="346e2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="346e2-107">Remarks</span></span>  
 <span data-ttu-id="346e2-108">Přidělenou paměť bude zahájena v adresu větší než bázové adresy modul, který je přidružen toto přidělení.</span><span class="sxs-lookup"><span data-stu-id="346e2-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="346e2-109">Jinými slovy každý allocator se vytvoří pro konkrétního modulu a pokusí se přidělit paměť na kladné posunu z jeho základní adresu.</span><span class="sxs-lookup"><span data-stu-id="346e2-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="346e2-110">Pokud `Alloc` nepodaří přidělit požadovaný počet bajtů na adresu větší než základní adresu modulu, vrátí E_OUTOFMEMORY, bez ohledu na skutečné množství paměti místa.</span><span class="sxs-lookup"><span data-stu-id="346e2-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>  
  
 <span data-ttu-id="346e2-111">`Alloc` Metoda má být použita ve spojení s [icorprofilerinfo::setilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="346e2-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="346e2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="346e2-112">Requirements</span></span>  
 <span data-ttu-id="346e2-113">**Platformy:** WindSee [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="346e2-113">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="346e2-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="346e2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="346e2-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="346e2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="346e2-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="346e2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="346e2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="346e2-117">See Also</span></span>  
 [<span data-ttu-id="346e2-118">IMethodMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="346e2-118">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
