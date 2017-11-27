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
ms.openlocfilehash: 34da00bdc33a836e5f459e6e4314f252e1e39e9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="26f39-102">ICorProfilerInfo7::GetInMemorySymbolsLength – metoda</span><span class="sxs-lookup"><span data-stu-id="26f39-102">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>
<span data-ttu-id="26f39-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="26f39-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="26f39-104">Vrátí délku datového proudu symbolu v paměti.</span><span class="sxs-lookup"><span data-stu-id="26f39-104">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f39-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26f39-105">Syntax</span></span>  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26f39-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="26f39-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="26f39-107">[v] Identifikátor modul, který obsahuje datový proud v paměti.</span><span class="sxs-lookup"><span data-stu-id="26f39-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="26f39-108">pCountSymbolBytes</span><span class="sxs-lookup"><span data-stu-id="26f39-108">pCountSymbolBytes</span></span>  
 <span data-ttu-id="26f39-109">[out] Ukazatel na `DWORD` hodnotu, která po návratu metody obsahuje délka datového proudu v bajtech.</span><span class="sxs-lookup"><span data-stu-id="26f39-109">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26f39-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="26f39-110">Return Value</span></span>  
 <span data-ttu-id="26f39-111">Vrátí metoda `S_OK` Pokud délka datového proudu paměti můžete určit, i když je nula (0).</span><span class="sxs-lookup"><span data-stu-id="26f39-111">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="26f39-112">Vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC` Pokud metoda byla vytvořena pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26f39-112">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26f39-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26f39-113">Remarks</span></span>  
 <span data-ttu-id="26f39-114">Pokud má modul symboly v paměti, délka datového proudu je umístěn v `pCountSymbolBytes`.</span><span class="sxs-lookup"><span data-stu-id="26f39-114">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="26f39-115">Pokud modul nemá symboly v paměti `*pCountSymbolBytes = 0`.</span><span class="sxs-lookup"><span data-stu-id="26f39-115">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26f39-116">Aktuální implementace Reflection.Emit nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="26f39-116">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="26f39-117">Pokud modul byl vytvořen pomocí Reflection.Emit, vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="26f39-117">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26f39-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26f39-118">Requirements</span></span>  
 <span data-ttu-id="26f39-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f39-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26f39-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="26f39-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26f39-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26f39-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26f39-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26f39-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f39-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="26f39-123">See Also</span></span>  
 [<span data-ttu-id="26f39-124">ICorProfilerInfo7 rozhraní</span><span class="sxs-lookup"><span data-stu-id="26f39-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
