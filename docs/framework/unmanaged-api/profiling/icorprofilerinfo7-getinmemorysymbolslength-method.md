---
title: "ICorProfilerInfo7::GetInMemorySymbolsLength – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type: COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c1299429e9173069c5a39fe4a2b82d1db5938f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="5d0b4-102">ICorProfilerInfo7::GetInMemorySymbolsLength – metoda</span><span class="sxs-lookup"><span data-stu-id="5d0b4-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="5d0b4-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="5d0b4-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="5d0b4-104">Vrátí délku datového proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="5d0b4-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d0b4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d0b4-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d0b4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d0b4-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="5d0b4-107">[v] Identifikátor modul, který obsahuje datový proud v paměti.</span><span class="sxs-lookup"><span data-stu-id="5d0b4-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="5d0b4-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="5d0b4-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="5d0b4-109">[out] Ukazatel na `DWORD` hodnotu, která po návratu metody obsahuje délka datového proudu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="5d0b4-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d0b4-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5d0b4-110">Return Value</span></span>  
 <span data-ttu-id="5d0b4-111">Vrátí metoda `S_OK` Pokud délka datového proudu paměti můžete určit, i když je nula (0).</span><span class="sxs-lookup"><span data-stu-id="5d0b4-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="5d0b4-112">Vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC` Pokud metoda byla vytvořena pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d0b4-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d0b4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d0b4-113">Remarks</span></span>  
 <span data-ttu-id="5d0b4-114">Pokud má modul symboly v paměti, délka datového proudu je umístěn v `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="5d0b4-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="5d0b4-115">Pokud modul nemá symboly v paměti `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="5d0b4-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d0b4-116">Aktuální implementace Reflection.Emit nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="5d0b4-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="5d0b4-117">Pokud modul byl vytvořen pomocí Reflection.Emit, vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="5d0b4-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d0b4-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d0b4-118">Requirements</span></span>  
 <span data-ttu-id="5d0b4-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d0b4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d0b4-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d0b4-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d0b4-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d0b4-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d0b4-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d0b4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d0b4-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d0b4-123">See Also</span></span>  
 [<span data-ttu-id="5d0b4-124">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d0b4-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
