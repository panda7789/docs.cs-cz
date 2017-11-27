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
ms.openlocfilehash: ae0fa84c08cb8e366db36b6727a3058f24789801
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmallocalloc-method"></a><span data-ttu-id="73e09-102">IMethodMalloc::Alloc – metoda</span><span class="sxs-lookup"><span data-stu-id="73e09-102">IMethodMalloc::Alloc Method</span></span>
<span data-ttu-id="73e09-103">Pokusí se přidělit zadanou velikost paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="73e09-103">Attempts to allocate a specified amount of memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73e09-104">Syntax</span></span>  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73e09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73e09-105">Parameters</span></span>  
 `cb`  
 <span data-ttu-id="73e09-106">[v] Počet bajtů k přidělení pro tělo metoda.</span><span class="sxs-lookup"><span data-stu-id="73e09-106">[in] The number of bytes to allocate for the method body.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73e09-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73e09-107">Remarks</span></span>  
 <span data-ttu-id="73e09-108">Přidělenou paměť bude zahájena v adresu větší než bázové adresy modul, který je přidružen toto přidělení.</span><span class="sxs-lookup"><span data-stu-id="73e09-108">The allocated memory will begin at an address greater than the base address of the module that is associated with this allocator.</span></span> <span data-ttu-id="73e09-109">Jinými slovy každý allocator se vytvoří pro konkrétního modulu a pokusí se přidělit paměť na kladné posunu z jeho základní adresu.</span><span class="sxs-lookup"><span data-stu-id="73e09-109">In other words, each allocator is created for a particular module, and will attempt to allocate memory at a positive offset from its base address.</span></span> <span data-ttu-id="73e09-110">Pokud `Alloc` nepodaří přidělit požadovaný počet bajtů na adresu větší než základní adresu modulu, vrátí E_OUTOFMEMORY, bez ohledu na skutečné množství paměti místa.</span><span class="sxs-lookup"><span data-stu-id="73e09-110">If `Alloc` fails to allocate the requested number of bytes at an address greater than the base address of the module, it returns E_OUTOFMEMORY, regardless of the actual amount of memory space available.</span></span>  
  
 <span data-ttu-id="73e09-111">`Alloc` Metoda má být použita ve spojení s [icorprofilerinfo::setilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="73e09-111">The `Alloc` method should be used in conjunction with the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73e09-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73e09-112">Requirements</span></span>  
 <span data-ttu-id="73e09-113">**Platformy:** WindSee [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73e09-113">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73e09-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73e09-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73e09-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73e09-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73e09-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73e09-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e09-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="73e09-117">See Also</span></span>  
 [<span data-ttu-id="73e09-118">Imethodmalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73e09-118">IMethodMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
